# Exchange overview

## High level overview

At a high level, 0xFlazh functions just like a normal exchange. Unlike a traditional exchange, which has all of its business logic defined and executed on a private server owned by a company, 0xFlazh's business logic is defined and executed in a smart contract on the public, decentralized [Ethereum](https://ethereum.org) blockchain. The 0xFlazh GUI (Graphical User Interface) is designed to let you interact with the 0xFlazh smart contract without having to deal with the low-level details of blockchain transactions.

Like any other exchange, 0xFlazh has an order book of resting orders. A resting order consists of a price, volume, expiration time (measured in blocks), and signature. In effect, it represents a signed intent to trade. When you create a new resting order, it gets broadcast to an off-chain order book server. The primary benefit of storing resting orders off-chain is that you don't have to create an Ethereum transaction and pay gas to submit a resting order. 0xFlazh does have a backup mechanism that allows orders to be submitted with on-chain transactions.

## Trading

When a counterparty decides to trade your resting order, he submits a transaction to the smart contract with your signed intent to trade and the volume he wishes to trade. The smart contract checks the signature, makes sure you and the counterparty both have enough funds to cover the trade, and then executes the trade by moving funds between accounts.

## Fees

The fees are based on marker and taker model (0.1% for takers, 0.05% for makers), and the admin account is only allowed to decrease the fees.
Previously, take fees were paid in the token being received by the taker. Now they (along with make fees and rebates) are paid in the token being given by the taker. This simplifies the fee calculus.


## Deposit & Withdrawal

The 0xFlazh smart contract allows you to deposit or withdraw Ether or any [ERC-20](https://github.com/ethereum/EIPs/issues/20) Ethereum token.