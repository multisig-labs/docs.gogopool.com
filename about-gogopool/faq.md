## **FAQ**

### What is Avalanche?

Avalanche is a new blockchain created by Ava Labs, and solves the [Trilemma](https://medium.com/certik/the-blockchain-trilemma-decentralized-scalable-and-secure-e9d8c41a87b3). It is:

1. Secure
2. Decentralized
3. Fast

If Bitcoin and Ethereum are L1s, Avalanche is an L0 and an L1. Any L1 can be created on top of Avalanche, inheriting the platform’s properties and allowing builders to focus on customizing the L1 to their own purposes.

### What is a subnet?

[Tweet storm on Subnets](https://twitter.com/das_connor/status/1456592161420587017)

Subnets are Avalanche’s secret weapon. They allow anyone to create a new L1, which can also operate as an L2. Subnets are mega cool because they represent everything we know about scaling blockchains in one interoperable package — imagine a network of blockchains that are small enough to be fast, but all assets on one blockchain is compatible with every other blockchain.

Avalanche’s C-Chain is an example of one subnet. It serves as a blockchain that is optimized for running smart contract code.

### What is staking?

In Proof of Stake blockchains, validator nodes do work to validate the blockchain and in return earn staking rewards.

For Avalanche, a staker must set up their hardware to validate the chain and put up a minimum of 2000 AVAX as their stake. The AVAX is locked up for the duration of the staking window, and accrues rewards. After the staking window (max of 1 year), the AVAX is returned as well as any staking rewards they earned.

### What is liquid staking?

Liquid staking is an alternative to locking up a user’s stake!

It allows anyone to effectively stake any amount of AVAX, and receive instant liquidity via a wrapped AVAX token. This wrapped token can be spent like normal AVAX, and can be exchanged for normal AVAX at any time.

### How is GoGoPool different from Lido?

There are a few differences.

1. Lido is a (very successful) liquid staking protocol.
2. Lido centralizes their hardware providers.
3. A Lido-like staking protocol only provides liquidity to stakers, and does not help bring about the promised future of subnets.

In contrast, GoGoPool:

1. Is a permissionless staking protocol.
2. Decentralizes hardware operators via community rewards.
3. Allows subnets to join the pool, incentivizing hardware operators to validate the subnet.

Avalanche has a big liquid staking problem (60% of AVAX is currently locked up in staking windows), but an even bigger subnet problem (only 17 subnets in production).

Lido solves the first problem, but we are doing the hard thing and making a protocol that solves both.

### Why doesn’t this exist yet?

I think there are a few reasons why this does not exist yet:

1. Avalanche is extremely new and people haven’t had time to build
2. People are working on it now, but builders are busy fundraising
3. It’s an extremely technical problem and not many people understand both Avalanche and liquid staking deeply enough to solve it

### How did you come up with the idea for GoGoPool?

I wanted to create and launch subnets on Avalanche which allows creators to incentivize their fans to grow the creator’s business using community DAOs.

But launching and growing a subnet is super expensive — each validator has to also validate the Avalanche chain, and I didn’t have a way to contact existing nodes to pick up my chain for validation. So I went to run my own validator node, and saw that each node must have a minimum stake of 2000 AVAX - making growing the subnet unfeasible, and locking me out of experimenting with the idea!

After doing research and seeing that no staking protocol was even close to existing, I decided to do something about it.

GoGoPool lets the next entrepreneur focus on their vision instead of having to worry about the node infrastructures of their blockchain.
