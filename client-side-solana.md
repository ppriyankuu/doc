# Solana wallet adapter, Client side Solana
### What are Wallet Adapters?
When building a dApp (decentralised application), you need a way for users to connect their wallets to your website. Wallet adapters provide a standardised interface that allows dApps to securely interact with various types of wallets.

##### How Wallet Adapters work
- Secure Communication :
    - Wallet adapters enable secure communication between dApp and the user's wallet without exposing private keys to the website.
    - The wallet retains full control over the private keys and user can approve or reject transaction requests sent by the dApp.
- Transaction Process - When a user intiates a transaction on a dApp, the wallet adapter facilitates the transaction by requesting user's wallet to approve it. The wallet then signs the transaction, ensuring only authorised actions are taken.

##### Why use Wallet Adapters?
- Multi-Wallet support - Wallet adapters make it easy for dApps to support multiple wallets that adhere to a common protocol, allowing for broader compatability.
- Simplified Integration: Developers can integrate different wallets into their dApp without needing to write custom code for each one, reducing complexity and speeding up development.

###### Examples in Action
- Explore this [demo](https://anza-xyz.github.io/wallet-adapter/example/) to see how wallet adapter connects a wallet to a dApp.
- Real-world dApps - Examples of dApps that use wallet adapters include [Tensor | Solana's leading NFT marketplace](https://www.tensor.trade/) and [Uniswap interface](https://app.uniswap.org/).

##### Common Actions in a dApp
Once a user connects their wallet to your dApp, there are several common actions they might perform :
1. Request Airdrop - Users might receive free tokens as an incentive or promotion from the mainnet or test SOL from the devnet.
2. Show SOL Balances - Fetch and display the user's SOL balances from the blockchain.
3. Send a transaction - Allow users to send transactions, such as transferring tokens to another wallet.
4. Sign a Message - Verify wallet ownership by asking the user to sign a message. 

### Requesting Airdrop with a React App
To build a React app for requesting a Solana airdrop (example: [click me!!!](https://solfaucet.com)), follow these steps :
1. Create a basic wallet connection in your `App.jsx` :
```javascript
    import React, { useMemo } from "react";
    import {
        ConnectionProvider,
        WalletProvider,
    } from "@solana/wallet-adapter-react";
    import { WalletAdapterNetwork } from "@solana/wallet-adapter-base";
    import {
        WalletModalProvider,
        WalletDisconnectButton,
        WalletMultiButton,
    } from "@solana/wallet-adapter-react-ui";
    import { clusterApiUrl } from "@solana/web3.js";
    import "@solana/wallet-adapter-react-ui/styles.css";


    function App() {
    const network = WalletAdapterNetwork.Devnet;

    const endpoint = useMemo(() => clusterApiUrl(network), [network]);

    return (
        <ConnectionProvider endpoint={endpoint}>
            <WalletProvider wallets={[]} autoConnect>
                <WalletModalProvider>
                    <div style={{ display: "flex", justifyContent: "space-between" }}>
                        <WalletMultiButton />
                        <WalletDisconnectButton />
                    </div>
                </WalletModalProvider>
            </WalletProvider>
        </ConnectionProvider>
    );
    }

    export default App;
```
- Replace `endpoint` with your RPC URL, e.g., `https://api.devnet.solana.com`

2. Create the Airdrop Component
- Add an `Airdrop` component to handle requesting airdrops.
```javascript
    import { useWallet } from "@solana/wallet-adapter-react";
    import { useConnection } from "@solana/wallet-adapter-react";
    import { LAMPORTS_PER_SOL } from "@solana/web3.js";

    export function RequestAirdrop() {
    const wallet = useWallet();
    const { connection } = useConnection();

    async function requestAirdrop() {
        let amount = document.getElementById("amount").value;
        await connection.requestAirdrop(
        wallet.publicKey,
        amount * LAMPORTS_PER_SOL
        );
        alert("Airdropped " + amount + " SOL to " + wallet.publicKey.toBase58());
    }

    return (
        <div>
            <br />
            <br />
            <input id="amount" type="text" placeholder="Amount" />
            <button onClick={requestAirdrop}>Request Airdrop</button>
        </div>
    );
    }
```
- This component requests an airdrop when the user clicks on the button, assuming their wallet is connected.
![image01](./images/testing-airdrop-request-through-react-app.avif)

3. Integrate Airdrop Component
- Include the `RequestAirdrop` component in you main `App.jsx`
4. If not familiar with the Context API and Props and to understand how the `ConnectionProvider` and `WalletProvider` work, you may need to familiarise yourself with React's Context API, prop drilling, and providers.

### Showing User Balance
Fetch and display the user's SOL balances from the blockchain.
```javascript
    import { useConnection, useWallet } from "@solana/wallet-adapter-react";
    import { LAMPORTS_PER_SOL } from "@solana/web3.js";

    export function ShowSolBalance() {
    const { connection } = useConnection();
    const wallet = useWallet();

    async function getBalance() {
        if (wallet.publicKey) {
            const balance = await connection.getBalance(wallet.publicKey);
            document.getElementById("balance").innerHTML = balance / LAMPORTS_PER_SOL;
        }
    }

    getBalance();
    return (
        <div>
            <p>SOL Balance:</p> <div id="balance"></div>
        </div>
    );
    }
```

### Sending Solana
Send a transaction - Allow users to send transactions, such as transferring tokens to another wallet.
```javascript
    import { useConnection, useWallet } from "@solana/wallet-adapter-react";
    import {
        LAMPORTS_PER_SOL,
        PublicKey,
        SystemProgram,
        Transaction,
    } from "@solana/web3.js";

    export function SendTokens() {
    const wallet = useWallet();
    const { connection } = useConnection();

    async function sendTokens() {
        let to = document.getElementById("to").value;
        let amount = document.getElementById("amount").value;
        const transaction = new Transaction();
        transaction.add(
        SystemProgram.transfer({
            fromPubkey: wallet.publicKey,
            toPubkey: new PublicKey(to),
            lamports: amount * LAMPORTS_PER_SOL,
        })
        );

        await wallet.sendTransaction(transaction, connection);
        alert("Sent " + amount + " SOL to " + to);
    }

    return (
        <div>
            <input id="to" type="text" placeholder="To" />
            <input id="amount" type="text" placeholder="Amount" />
            <button onClick={sendTokens}>Send</button>
        </div>
    );
    }
```

### Sign a Message
Verify wallet ownership by asking the user to sign a message.
Purpose - Prove ownership of a wallet to a centralised backend by signing a message. This technique is used in various dApps, such a Tensor.
1. Install the Required Dependencies
    - To handle message signing, you need to install `@noble/curves` for cryptographic operations.
    ```bash
    $ npm install @noble/curves
    ```
2. Create the SignMessage Component
    - This component allows users to input a message and sign it using their connected wallet :
```javascript
    import { ed25519 } from "@noble/curves/ed25519";
    import { useWallet } from "@solana/wallet-adapter-react";
    import bs58 from "bs58";
    import React from "react";

    export function SignMessage() {
        const { publicKey, signMessage } = useWallet();

        const onClick = async () => {
            if (!publicKey) {
                alert("Wallet not connected!");
                return;
            }
            if (!signMessage) {
                alert("Wallet does not support message signing!");
                return;
            }

            const message = document.getElementById("message").value;
            const encodedMessage = new TextEncoder().encode(message);
            const signature = await signMessage(encodedMessage);

            if (!ed25519.verify(signature, encodedMessage, publicKey.toBytes())) {
                alert("Message signature invalid!");
                return;
                }
                alert(`Message signature: ${bs58.encode(signature)}`);
        };

        return (
            <div>
                <input id="message" type="text" placeholder="Message" />
                <button onClick={onClick}>Sign Message</button>
            </div>
        );
    }
```
- Explaination
    - Connect Wallet - Uses useWallet to access the user's wallet.
    - Sign Message - Signs the message entered by the user if the wallet supports it.
    - Verify Signature - Verifies the signature to ensure it matches the message and public key.
    - Alert - Displays the signed message's signature in Base58 encoding.

3. Integrate the Component into Your App
    - To use the `SignMessage` component, include it in your main `App.jsx` or any relevant component where wallet interaction is required.
