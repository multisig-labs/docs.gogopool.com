---
description: A Decentralized Staking Protocol For Avalanche Subnets.
---

# GoGoPool Primer

## Author

Original Author: Steven

Email: steven@multisiglab.org

Last Updated: 06 September 2022

## **TL;DR**

1. Subnets are Avalanche’s main scaling mechanism, but aren’t realistic right now because of the cost and limitations of staking
2. Liquid staking is just a small part of the problem, and everyone is focused on that (leaving builders out to dry)
3. GoGoPool solves the entire problem with a decentralized staking protocol combining liquid staking, decentralized hardware, and subnet compatibility. These three elements work together to trivialize the cost of staking + validating -- powering the growth of subnets, and the future of Avalanche

## **The Subnet Vision**

[Avalanche](https://www.avax.network/) promises to be a fast, low cost and eco friendly blockchain - thanks to **subnets.** Subnets let anyone build a blockchain without having to worry about its infrastructure, getting Avalanche’s best features for free.

As a single example: DeFi Kingdoms (the most popular blockchain game, lives on Harmony network) wants to launch an expansion to their game, but launching on Harmony is going to be expensive and slow for their users and they need more customization. They are launching a subnet on Avalanche, taking advantage of fast transaction times and with their own dedicated set of validators - leading to a fast and cheap experience for their users. Launching via subnets also lets DFK to experiment with tokenomics — tying the tokenomic of their blockchain directly to game mechanics.

Basically, subnets power the explosive growth of Avalanche by allowing infinite horizontal scaling and rapid experimentation with new models and ideas.

But in reality, subnets are expensive to start, grow and manage. Right now, they are held back by the cost and limitations of staking.

Ideally, every subnet should have a one-click launch and grow experience and not have to worry about their validators because the cost of staking is so low.

A handful of projects are focused on **liquid staking** as a way to lower the cost of staking on Avalanche, but they are focused on a small part of the problem. Having liquid staking will definitely help the ecosystem grow by providing liquidity, but does not lower the cost of validation for subnets. Entrepreneurs remain locked out of the next generation of opportunities, and Avalanche misses out on its next step function of growth.

We’re doing the hard thing, and building a decentralized staking protocol that has:

1. Decentralized hardware pools
2. Liquid staking
3. Subnet compatibility

Hardware operators join the protocol with 1000 AVAX, get matched with funds from liquid stakers, and begin validating the Avalanche Primary Network with the required 2000 AVAX (earning both staking and GGP community rewards). Stakers receive the benefit of liquid staking, getting a wrapped ggAVAX token and having instant liquidity while earning rewards in real time. Over time, the hardware operators in our protocol grows. When a subnet launches, they join our protocol by staking the GGP token and in return get access to the protocol’s validator marketplace. Subnets receive validators right away, eliminating their biggest upfront cost. Liquid stakers and subnets work together to incentivize hardware operators, lowering the cost of launching subnets further.

Subnets are a flywheel for our protocol - they do our best acquisition for us for free by incentivizing hardware operators to join, and we provide them with a liquidity pool and node operators to validate their subnet in exchange. This network effect at scale trivializes the cost of growing subnets for entrepreneurs, and leads to GoGoPool powering the explosive growth of Avalanche.

## **FAQ**

### What is Avalanche?

Avalanche is a new blockchain created by Ava Labs, and solves the [Trilemma](https://medium.com/certik/the-blockchain-trilemma-decentralized-scalable-and-secure-e9d8c41a87b3). It is:

1. Secure
2. Decentralized
3. Fast

If Bitcoin and Ethereum are L1s, Avalanche is an L0 and an L1. Any L1 can be created on top of Avalanche, inheriting the platform’s properties and allowing builders to focus on customizing the L1 to their own purposes.

### What is a subnet?

[Tweet storm on Subnets](https://twitter.com/das\_connor/status/1456592161420587017)

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
