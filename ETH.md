# Ethereum

## World State in Ethereum
![image01](./images/world-state-ETH.webp)

In simple terms, the World State in Ethereum is a giant list that keeps track of the current situation for every account on the network. This includes two types of accounts - 
1. Externally Owned Accounts (EOAs) - These are accounts that people control with their private keys; like personal wallets.
2. Contract Accounts - These are accounts controlled by smart contracts instead of a private key.

**So, What does the World State do?**
The World State maps each account's address (the unique identifier for each account) to its current state. Each account's state includes details like - 
- Balance - How much ETH the account holds.
- Storage - Any data stored in the account (especially for contract accounts).
- Code - For contract accounts, this includes the actual code that smart contract runs.
