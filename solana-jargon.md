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