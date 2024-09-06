# Introduction to SOLANA

### Beyond Bitcoin
#### Limitations of Bitcoin - 
- Bitcoin primarily serves as a decentralised currency.
- It was not designed to support complex applications or diverse use cases.

#### The Rise of alternative Blockchains -
- `Post-2012 Developments` - Various blockchains emerged, each tailored for specific purposes, such as lending protocols or decentralised exchanges.
- Challenges faced:
    - `Fragmentation` - Each blockchain operated independently with its own set of miners and consensus mechanisms.
    - `Cold start problem` - New blockchains struggled to gain traction and security, unablt to match bitcoin's network size and robustness.

### Ethereum: A Revolutionary solution
- Ethereum introduced the concept of `smart contracts`, allowing developers to build decentralised applications (dApps) directly on the Ethereum network.
- Advantages of Ethereum:
    - No cold start problem - Developers could leverage Ethereum's existing decentralised network, avoiding the intial growth challenges faced by standalone blockchains.

e.g. Counter Contract on `Solidity`:
```javascript
    // SPDX-License-Identifier: MIT
    pragma solidity ^0.8.0;

    contract Counter {
        uint public count;

        // Constructor to initialize count
        constructor() {
            count = 0;
        }

        // Function to increment the count
        function increment() public {
            count += 1;
        }

        // Function to decrement the count
        function decrement() public {
            require(count > 0, "Count cannot be negative");
            count -= 1;
        }
        
        // Function to get the current count
        function getCount() public view returns (uint) {
            return count;
        }
    }
```

### Solana: A new Frontier
- `Smart contracts vs Programs`: What Ethereum calls `smart contracts`, Solana refers to as `program`.
- Solana offers similar capabilities to Ethereum but with significantly faster transaction speeds and scalabilty, high throughput and low latency.
- The design and operation of solana's programs differ from traditional blockchains, providing a distinct approach to building and running decentralised applications.

### Accounts in Solana
##### What is an Account?
- In Solana, an account is a data structure that includes a public-private keypair (using the `ed25519` elliptic curve).
- Types of Accounts:
    - Wallet Accounts - These accounts represent user wallets that can hold `lamports` (Solana's native currency).
    - Data Accounts - These accounts store data on the blockchain and can be used for various decentralized applications.
    - Program Accounts - These are special accounts that store executable code, allowing smart contracts (known as "programs" in Solana) to run on the blockchain.

### Rent on Solana
- Purpose of Rent - To prevent the blockchain from being clogged with inactive or unnecessary data, Solana charges rent for storing data.
    - Rent Calculation - Rent is based on the storage size and the duration the account remains on the blockchain.
    - Rent Exemption - If an account maintains a balance above a certain threshold, it becomes "rent-exempt," meaning it does not incur further rent charges. The rent paid is refundable when the account is closed.

    [What is Rent on Solana, and how to calculate it](https://www.quicknode.com/guides/solana-development/getting-started/understanding-rent-on-solana)

### Efficient Storage Management
- Incentivizing Minimal Storage - The rent model encourages users to store only the necessary data, reducing blockchain bloat.
- Removing Inactive accounts - Accounts that fail to pay the required rent are eventually removed from the ledger, ensuring use of blockchain resources.