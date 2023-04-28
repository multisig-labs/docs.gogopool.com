# FAQ

## What is Avalanche?

Avalanche is a new blockchain created by Ava Labs, and solves the [Trilemma](https://medium.com/certik/the-blockchain-trilemma-decentralized-scalable-and-secure-e9d8c41a87b3). It is:

1. Secure
2. Decentralized
3. Fast

If Bitcoin and Ethereum are L1s, Avalanche is an L0 and an L1. Any L1 can be created on top of Avalanche, inheriting the platform’s properties and allowing builders to focus on customizing the L1 to their own purposes.

## What is a subnet?

[Tweet storm on Subnets](https://twitter.com/das\_connor/status/1456592161420587017)\
[Avalanche's Official Subnet Docs](https://docs.avax.network/subnets)

Subnets are Avalanche’s secret weapon. They are private blockchains, with batteries included. \
\
Through subnets, any user can effortlessly create a new L1 blockchain that is equipped to function seamlessly as an L2. Subnets are revolutionary, consolidating all our knowledge of blockchain scaling into a single, interoperable package. Picture a network of interconnected blockchains, each small enough to process transactions quickly, yet fully compatible with one another.&#x20;

Avalanche’s C-Chain is an example of one subnet. It serves as a blockchain that is optimized for running smart contract code.

## What is staking for node operators?

In Proof of Stake blockchains, validator nodes validate the blockchain and earn staking rewards as compensation.

For Avalanche, a node operator must set up their hardware to validate the chain and put up a minimum of 2000 AVAX as their stake. The AVAX is locked up for the duration of the staking window, and accrues rewards. After the staking window (max of 1 year), the AVAX is returned as well as any staking rewards they earned.

## What is liquid staking?

Liquid staking is an alternative to locking up a user’s stake!

It allows anyone to effectively stake any amount of AVAX, and receive instant liquidity via a wrapped AVAX token. This wrapped token can be spent like normal AVAX, and can be exchanged for normal AVAX at any time.

## How is GoGoPool different from Lido?

There are a few differences.

1. Lido is a (very successful) liquid staking protocol.
2. Lido centralizes their hardware providers.
3. A Lido-like staking protocol only provides liquidity to stakers, and does not help bring about the promised future of subnets.

In contrast, GoGoPool:

1. Is a permissionless staking protocol.
2. Decentralizes hardware operators via community rewards.
3. Allows subnets to join the pool, incentivizing hardware operators to validate the subnet.

Avalanche has a big liquid staking problem (60% of AVAX is currently locked up in staking windows), but an even bigger subnet problem (only 17 subnets in production).

While Lido addresses the first problem, we have set out to tackle the more challenging task of developing a protocol that provides a solution for both issues at hand.



## How did you come up with the idea for GoGoPool?

Steven wanted to create and launch subnets on Avalanche which allows creators to incentivize their fans to grow the creator’s business using community DAOs.

But launching and growing a subnet is super expensive — each validator has to also validate the Avalanche chain, and he didn’t have a way to contact existing nodes to pick up my chain for validation. So he went to run his own validator node, and saw that each node must have a minimum stake of 2000 AVAX - making growing the subnet unfeasible, and locking me out of experimenting with the idea!

After doing research and seeing that no staking protocol was even close to existing, he decided to do something about it.

GoGoPool lets the next entrepreneur focus on their vision instead of having to worry about the node infrastructure of their blockchain.
