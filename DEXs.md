# Dentralized Exchanges
"Dex" stands for **Decentralized Exchanges**, which is a place where people can trade (buy or sell) cryptocurrencies directly with each other without using middleman, like a bank or traditional exchange.

### How is works in Blockchain
1. No middleman - There's no central entity managing the trades. You just use a platform (the marketplace) to find people willing to trade with you.

2. Smart Contracts - These are like automated stalls. You walk up to a stall, drop in your goods (cryptocurrency), and the smart contract ensures the trade happens safely and fairly with whoever wants to buy it. 

3. Direct Ownership - On a Dex, you own your cryptocurrency until the moment you decide to trade it. There's no central party holding it for you.

So, a Dex is basically a digital version of a farmer's market for trading cryptocurrencies without involving big intermediaries.

In simple terms, a DEX (Decentralized Exchange) is acryptocurrency trading platform that operateswithout a central authority, allowing users totrade assets directly with one another (peer-to-peer) using smart contracts.

# CEX
"Cex" stands for **Centralized Exchange**, which is an online platform where you can buy, sell, or trade cryptocurrencies, but this platform is run by a company that acts as a middleman to facilitate the trades.

### How it works in Blockchain
1. Middleman - The Cex (exchange) acts like the supermarket. It holds all the cryptocurrencies and manages the buying and selling for you. You deposit your money into their account, and they handle the trades.
2. Order Matching - When you want to buy or sell cryptocurrency, the Cex automatically matches your order with another user’s order, like how a supermarket restocks or sells items to customers.
3. Custody - When you trade through a Cex, you don’t actually hold your cryptocurrency directly. It’s more like putting money in your supermarket’s gift card; the exchange holds your crypto for you until you want to withdraw it.

So, a Cex is like a supermarket for cryptocurrencies where the company (the exchange) controls all the trading, matching, and storage of the assets. Unlike a Dex (the farmer’s market), here you rely on the supermarket (exchange) to handle everything for you.

## DEX vs CEX
![image01](./images/DEXvsCEX.webp)

## CEX Jargons
1. **Orderbooks**
An orderbook is like a menu board at a restaurant that lists all the buy and sell orders for a cryptocurrency in one place. It shows the prices people are willing to pay to buy (bids) and the prices at which others are willing to sell (asks).

2. **Bids**
Bids are the offers made by buyers to purchase a cryptocurrency at a specific price. 
In the CEX, bids are the prices that buyers are willing to pay for a particular cryptocurrency, listed in the orderbook.

3. **Asks**
Asks (or "offers") are the offers made by sellers who want to sell their cryptocurrency at a specific price.
In the CEX, asks are the prices that sellers are willing to accept for their cryptocurrency, and they also appear in the orderbook.

4. **Spread**
The spread is the difference between the highest bid price and the lowest ask price in the orderbook. It essentially shows the gap between what buyers are willing to pay and what sellers are willing to accept.

In CEX trading, a small spread usually means a more active market, while a large spread suggests less activity or fewer traders willing to agree on a price.

5. **Liquidity**
Liquidity refers to how easily and quickly you can buy or sell a cryptocurrency without affecting its price.

A market with high liquidity means you can quickly buy or sell large amounts of a cryptocurrency without much change in price. A market with low liquidity might make trades slower and lead to bigger price swings.

6. **Market Makers**
Market makers are traders or entities that add liquidity to the market by placing both buy (bid) and sell (ask) orders on the exchange. They help keep the market active and the spreads tight.

Market makers profit from the spread (the difference between their bid and ask prices) and help keep the market flowing smoothly.

**Summary**
so, all these terms play a role in understanding how a CEX works. Here's a quick recap -
- Orderbooks - A list of all buy and sell orders.
- Bids - Prices buyers are willing to pay.
- Asks - Prices sellers want to receive.
- Spread - The price gap between the highest bid and lowest ask.
- Liquidity - How easily you can trade without changing the price much.
- Market Makers - Entities that provide liquidity by always being ready to buy or sell.

### How does a DEX work?
1. **Peer-to-Peer Trading** - On a DEX, traders interact with each other to buy or sell assets. There is no middleman or central authority holding your funds or managing the trades. Instead, trades happen directly between users' wallets.

2. **Smart Contracts Automate trades** - A DEX uses smart contracts, which are self-executing programs on the blockchain. These contracts automatically execute the terms of a trade (like swapping one cryptocurrency for another) once the conditions are met.

3. **Token Swaps through Liquidity Pools** - Many DEXs use a model called *Automated Market Making* (AMM), which relies on Liquidity Pools. A liquidity pool is a collection of funds locked in a smart contract, and these funds are used to enable trading between cryptocurrency pairs (like swapping ETH or USDT).

4. **No Custody over your funds** - On a DEX, you retain full control over your cryptocurrency throughout the trade. You use a crypto wallet (like Backpack or Phantom) to connect directly to the DEX and approve transactions.

5. **Transparency and Security** - Because trades are executed on the blockchain and controled by smart contracts, everything is transparent and verifiable. You can see the trade history, liquidity pool balances, and smart contract codes. Plus, since there is no central point of failure, it's often more secure from hacks targeting centralised entities. 

**Common examples of DEXs**
- Uniswap - A popular Ethereum-based DEX that uses the AMM model with liquidity pools.
- SushiSwap - A fork of Uniswap with additional features.
- PancakeSwap - A DEX built on the Binance Smart Chain with similar functionality to Uniswap.

#### How Pricing Works in DEXs
In DEXs, there is no centralised orderbook to match buyers and sellers. Instead, algorithms determine the price of assests based on liquidity pools. One of the most common algorithms used is the Constant Product Market Maker (CPMM) model, which is based on a simple formula.

`X * Y = K`

- *x* and *y* represent the quatities of two different tokens in a liquidity pool (e.g. ETH and USDT).
- *k* is a constant product, meaning it always stays the same.
This formula essentially says that the product of the two token quantities (x and y) must remain constant. When someone makes a trade, the balance of tokens in the pool changes, which in turn, changes the price.