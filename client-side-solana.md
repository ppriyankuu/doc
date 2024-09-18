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