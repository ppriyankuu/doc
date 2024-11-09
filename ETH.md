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

#### Account types in ETH (EOA vs Contract Accounts)
*Externally Owned Accounts (EOAs)*
EOAs are like personal wallets on the Ethereum network.

*Putting it all together*
In Ethereum, an EOA is like personal bank account with a PIN code that you control. You can send ETH to others, receive ETH, and interact with smart contracts, but you're the one who starts all actions. It's a straightforward account with not extra features, just like a bank account that holds your money and lets you send it whenever you want.

*Contract Account*
In Ethereum, Contract Accounts are special accounts that are governed by code (smart contracts) instead of being controlled by private keys like Externally Owned Accounts (EOAs). Here's a closer look at their characterstics and what makes them unique -
1. Controlled by Code (Smart contracts)
    - Contract Accounts are managed by the smart contract code they contain. This means they don't have private keys and connot by directly accessed by a person. Instead, they operate based on the code that was set up when they were created.
2. Cannot Initiate Transactions 
    - Contract Accounts can't start transactions on their own. They can only respond to incoming transactions from EOAs or other contracts. So, an EOA needs to interact with the Contract Account first to "wake it up".
    - Once they receive a transaction, they can execute functions, udpate internal data, or ever interact with other contracts if programmed to do so.
3. Contains Smart contract code 
    - The smart contract code inside a contract Account can perform complex tasks. This code can contain ruls for various financial applications, manage business logic, or execute complex computations.
    - The code is usually written is Solidity (a programming language for Ethereum) and deployed to the blockchain, where it becomes permanent.
4. Ether balance
    - Like EOAs, contract accounts can hold ETH. However, they can only spend or transfer it based on the logic written in the smart contract. For example, a contract might only release ETH if specific conditions are met.
5. Gas costs
    - Executing functions in a Contract Account requires gas (paid in ETH). The gas fee is paid by the EOA initiating the transaction. If a contract function calls other contracts, it may use even more gas, and the EOA initiating the transaction covers this cost.
6. Permanent Deployment
    - Once a smart contract is deployed to the Ethereum blockchain, it’s immutable—meaning it can’t be modified or deleted. This ensures that the contract’s rules remain consistent, but it also means that any mistakes in the code are permanent.