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

#### Real-Life Example
Imagine you have a *gym locker* at a gym. In this analogy:
- Your locker number (key) is unique, just like each Solana has a unique *address*.
- Inside your locker, you might store gym clothes (data) or instructions for workout (program code).
- You pay rent for using the locker, but if you stop using it, you get your deposit back.
- Only you (the owner) can open the locker and change what's inside, but someone else can still add money to your locker.


In simple terms, on solana, all data is stored in what are reffered to as "accounts". The way data is organised on Solana resembles a [key-value store](https://en.wikipedia.org/wiki/Key%E2%80%93value_database), where each entry in the database is called as "account".

#### What is an Account?
In solana, an account is like a mailbox where you store data. Each account has a unique address, which is like your mailbox's number. This address is 32 bytes long and works like a public key (using the Ed25519 cryptography standard), making it secure.

*Account Info*
1. *Data (Bytes)*
- This is the actual information stored in the account, like letters or packages you put in the mailbox. The data is stored as a series of bytes.
2. *Executable (Boolean)*
- A simple *yes* or *no* values (true/false) that tells if the account contains executable code, like instructions for doing something (similar to having a manual in your mailbox).
3. *Lamports (Number)*
- This represents how many lamports (Solana's smallest unit of currency) the account holds. Think of lamports like money stored in the mailbox.
4. *Owner (Program Address)*
- This is the owner of the account, usually a program that controls what happens with the data inside. It's like having the person or entity responsible for that mailbox.

##### System Program
Solana contains a small handful of native programs that are part of the validator implementation and provide various core functionalities for the network.

*Solana's Native Programs*
On Solana, there are few built-in programs that help the network function. Think of these as essential services that keep everything running smoothly. The two most important ones you'll deal with when creating your own programs are the *System Programs* and the *BPF loader*.