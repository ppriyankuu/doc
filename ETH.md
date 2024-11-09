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

**Simple Analogy**
Think of the World State as a spreadsheet where each row represents an account, and each column holds teh current details about the account. Whenever a transaction happens, this spreadsheet updates with the new balances, data, and any other changes.

So, the World State is the complete picture of the what every account on Ethereum currently "looks like" at any given moment.

**ETH as a State Machine**
Ethereum is a state machine whose state changes as more blocks are added to the blockchain. This means that Ethereum constantly updates its World State (the current situation of all accounts) whenever a new block of transactions is added.

![image02](./images/account-register-ETH.webp)

The small box in the image represents an example of the World State at a specific point -
- Each account (like Account01, Account02, etc.) has a balance (e.g., 1.1 ETH, 2 ETH).
- When a new transaction is processed, these balances can change, reflecting the new state of Ethereum.

So, each time a new block is added, Ethereum's "state" updates to match the latest transactions, moving teh system to a fresh snapshot of all account balances and contract data. This is what it means for Ethereum to work like a "state machine".

