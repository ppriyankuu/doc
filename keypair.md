# Creating a public/private keypair
Lets look at various ways of creating public/private keypairs, signing messages and verifying them.

### EdDSA - Edwards-curve Digital Signature Algorithm  - ED25519
Using `@noble/ed25519`
```javascript
    import * as ed from "@noble/ed25519";

    async function main() {
        // Generate a secure random private key
        const privKey = ed.utils.randomPrivateKey();

        // Convert the message "hello world" to a Uint8Array
        const message = new TextEncoder().encode("hello world");

        // Generate the public key from the private key
        const pubKey = await ed.getPublicKeyAsync(privKey);

        // Sign the message
        const signature = await ed.signAsync(message, privKey);

        // Verify the signature
        const isValid = await ed.verifyAsync(signature, message, pubKey);

        // Output the result
        console.log(isValid); // Should print `true` if the signature is valid
    }
    main();
```

Using `@solana/web3.js`
```javascript
    import { Keypair } from "@solana/web3.js";
    import nacl from "tweetnacl";

    // Generate a new keypair
    const keypair = Keypair.generate();

    // Extract the public and private keys
    const publicKey = keypair.publicKey.toString();
    const secretKey = keypair.secretKey;

    // Display the keys
    console.log("Public Key:", publicKey);
    console.log("Private Key (Secret Key):", secretKey);

    // Convert the message "hello world" to a Uint8Array
    const message = new TextEncoder().encode("hello world");

    const signature = nacl.sign.detached(message, secretKey);
    const result = nacl.sign.detached.verify(
        message,
        signature,
        keypair.publicKey.toBytes(),
    );

    console.log(result);
```

### ECDSA (Elliptic Curve Digital Signature Algorithm) - secp256k1
Using `@noble/secp256k1`
```javascript
    import * as secp from "@noble/secp256k1";

    async function main() {
        const privKey = secp.utils.randomPrivateKey(); // Secure random private key
        // sha256 of 'hello world'
        const msgHash =
            "b94d27b9934d3e08a52e52d7da7dabfac484efe37a5380ee9088f7ace2efcde9";
        const pubKey = secp.getPublicKey(privKey);
        const signature = await secp.signAsync(msgHash, privKey); // Sync methods below
        const isValid = secp.verify(signature, msgHash, pubKey);
        console.log(isValid);
    }
    main();
```

Using `ethers`
```javascript
    import { ethers } from "ethers";

    // Generate a random wallet
    const wallet = ethers.Wallet.createRandom();

    // Extract the public and private keys
    const publicKey = wallet.address;
    const privateKey = wallet.privateKey;

    console.log("Public Key (Address):", publicKey);
    console.log("Private Key:", privateKey);

    // Message to sign
    const message = "hello world";

    // Sign the message using the wallet's private key
    const signature = await wallet.signMessage(message);
    console.log("Signature:", signature);

    // Verify the signature
    const recoveredAddress = ethers.verifyMessage(message, signature);

    console.log("Recovered Address:", recoveredAddress);
    console.log("Signature is valid:", recoveredAddress === publicKey);
```
