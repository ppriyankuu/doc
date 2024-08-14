# How do Transactions work on the blockchain?
[reference](https://andersbrownworth.com/blockchain/) <br />

### User side
- User first creates a public/private keypair
- They create a `transaction` that they want to do (send $50 to Jhon Doe). The transaction includes all the necessary details like the recipient's address, the amount, and some blockchain specific parameters (like the latest block-hash in case of solana).
- They hash the transaction.
- They `sign` the transaction using the private key
- They send the `raw transaction`, `signature`, and the `public key` to a node on the blockchain.

### Miner
- Hashes the original message to generate a hash
- Verifies the `signature` using the user's `public key` and the `hash` generated before.
- Transaction validation - The miner/validator checks additional aspects of the transaction, such as that the user has sufficient funds.
- If everything checks out, miner adds the transaction to the block.