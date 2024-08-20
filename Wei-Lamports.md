# Wei, Lamports

## ETH
Wei: The smallest unit of cryptocurrency in the Ethereum network. It's similar to how a cent is to a dollar.
 - Value : 1 Ether (ETH) = 10^8 Wei.

Gwei: A larger unit of Ether commonly used in the context of gas prices.
 - Conversion: 1 Ether = 10^9 gwei.

### Lamports
- In the Solana blockchain, the smallest unit of currency is called a `lamport`. Just as wei is to Ether in Ethereum, lamports are to SOL (the native token of solana).
- 1 SOL = 10^9 Lamports

```javascript
    const { LAMPORTS_PER_SOL } = require("@solana/web3.js");
    console.log(LAMPORTS_PER_SOL);
```
