# Accounts
On Solana, all the data is stored in what are referred to as `accounts`. The way data is organised on Salana resembles a key-value store, where each entry in the database is called an 'account'.

![image01](./images/accounts-solana.avif)

#### Key points
- Accounts can store up to 10mb of data, which can consist of either executable program code or program state.
    - Programs (smart contracts) are stateless accounts that store executable code.
    - Data accounts are created by programs to store and manage program state.
- Accounts require a rent deposit in SOL, proportional to the amount of data stored, which is fully refundable when the account is closed.
- Every account has a program `owner`. Only the program that owns an account can modify its data or deduct its lamport balance. However, anyone can increase the balance.
- Native programs are built-in programs included with the Solana runtime.