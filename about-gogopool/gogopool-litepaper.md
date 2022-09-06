---
description: Our goals and a brief overview of the protocol.
---

# GoGoPool Litepaper

## Author

Author: Steven

Email: steven@multisiglab.org

Last Updated: 06 September 2022

Editor: Chandler

Editor Email: chandler@multisiglabs.org

## **Abstract**

GoGoPool allows Avalanche users to stake a minimum of 0.01 AVAX and operate a validator node with a minimum of 1000 AVAX, while providing instant liquidity and earning rewards for validating subnets. As an open protocol, any individual, business, or subnet can plug into the protocol without being charged platform fees. The goal of GGP is to trivialize the cost of starting, growing, and managing subnets for future builders while democratizing validating and staking. Our mission is to be the model base layer protocol group that inspires future web3 projects.

## **Introduction**

Avalanche aims to be a blazingly fast, eco friendly, and low-fee platform that any L1 may build on. They achieve this with a horizontal scaling technique called **subnets**.

At a high level, subnets are any L1 chain that builds on top of Avalanche’s platform (inheriting Avalanche’s best properties for free).

The problem is that subnets are too expensive to start, grow and manage. Every validator of a subnet must also validate the Avalanche Primary Network (which requires paying 2000 AVAX as a minimum staking amount, and managing your own hardware).

For builders that wish to experiment with building new subnets on top of Avalanche, the cost of paying 2000 AVAX per node and managing all the hardware is prohibitively high.

GoGoPool aims to trivialize the cost of starting, growing and managing a subnet with an open staking protocol that has built in subnet compatibility - enabling rapid experimentation with new business models and ideas in the Avalanche ecosystem.

## **Goals**

Our goal is to be the primary go-to staking protocol for Avalanche with a decentralized, trustless and peerless staking network that is easy to use for both individuals, businesses, and subnets. This has 3 components: 1) liquid staking 2) decentralized hardware operators and 3) subnet compatibility.

\- Democratize and decentralize the state of Avalanche staking + validation

\- Ensure that staking infrastructure and components are as decentralized, trustless and scalable as possible

\- Minimize deposit risk by socializing staking losses and rewards across the network

\- Decentralize GGP development, governance, and security using GGP tokenomics to create healthy self sustaining community\
\- Create a scalable network that can support Avalanche’s insane growth, both now and in the long term future

\- Trivialize the cost of starting, growing, and managing a subnet’s infrastructure

\- Inspire future projects by being a model example of a web3 protocol, helping proliferate the web3 ethos in the developer community

## **Protocol Overview**

The GoGoPool protocol emphasizes trustlessness and peerlessness wherever possible, to maximize its decentralization, security, and scalability.

There are 3 main components to the protocol: the users, community(tokenomics/DAO), and custom node software.

### **Users Primer**

There are three main users of the GoGoPool protocol, all with their own use cases.

#### Node Operators

Contribute their own hardware to the pool, and stake a minimum of 1000 AVAX. Operators maintain their server infrastructure, and are matched with the other 1000 AVAX from a deposit pool of stakers. Operators charge a small operating fee (not unlike the existing delegator fee) for the use of the hardware, and are also incentivized with GGP tokens to maintain good behaviour. This allows a node operator to begin staking with less AVAX than is normally required, earn rewards on their staked AVAX, and earn rewards via the operating fee and network rewards.

Node operators run our custom node software, which includes the Avalanche Client (to handle staking) and the GoGoPool client (to handle registration/interacting with the protocol).

This triple incentive structure allows them to earn much higher rewards than staking solo, while providing hardware to the pool.

#### Liquid Stakers

Liquid Stakers (hereby referred to as just "Stakers") are either individuals or users from an API integrated business. Stakers deposit AVAX into the deposit pool, and are instantly assigned gAVAX (our synthetic derivative token) to provide instant liquidity which accrues value over time based on the performance of the protocol. The deposited AVAX is automatically assigned to node operators for staking.

Stakers are given access to instant liquidity, being able to use gAVAX in any place AVAX could be used. But unlike AVAX, ggAVAX increases in value over time based on the performance of the pool - while not needing to trust any individual node operator (in contrast to the current delegator system, where trust is an explicit requirement).

#### Subnets

Subnets that want to grow their network but do not have the means to run their own validator nodes can incentivize node operators to validate the subnet. Node operators register on our marketplace, flagging their hardware as ‘available for validations’.

Subnets have access to an “AWS” marketplace-like interface, where they can choose what kind of hardware they need as validators, how much they are willing to pay (using the protocol token), and for how long they want the staking period to be.

After choosing their parameters and uploading their client to a repository, subnets are matched with available node operators automatically. The node operator’s software stack downloads the subnet’s client and begins validating the subnet, without requiring any human intervention from the node operator.

This further incentivizes node operators to join the protocol, increasing their payout with another income stream. In exchange, subnets get a massively reduced cost for launching, growing and managing the validator set for their subnet.

Anyone can safely become a staker for as little as .01 AVAX - including individuals or businesses. In this way, GoGoPool opens up the entire AVAX economy by providing much needed liquidity to stakers and DeFi apps in a trustless manner.

GoGoPool uses a mix of smart contracts and DAOs to achieve this level of decentralization, despite technical challenges that prevent a pure trustless solution.

### **Tokenomics Primer**

There is much room for innovation in community-driven organizations, and GoGoPool plans to be on the forefront.

We have two tokens: ggAVAX (liquid staking token described above), and GGP (protocol token used for DAO governance, rewards, insurance, and incentivizing long term behaviour).

#### **ggAVAX**

When a user deposits AVAX into the deposit pool, they receive a synthetic derivative token called ggAVAX.

ggAVAX represents a staker’s deposit plus the rewards it gains over time. This token is considered liquid and can be used in any way that AVAX is used. Users will be able to exchange gAVAX back for AVAX (which burns the ggAVAX, and draws AVAX from the deposit pool). Alternatively, they will have the option to list it on any exchange listing the token and exchange it for any token they would like.

#### **GGP**

GGP is an ERC20 token, and serves as the protocol token of GoGoPool.

Node Operators have to buy a minimum amount of GGP tokens to secure their stake as insurance of good behaviour. The minimum at genesis will be 10% of their staked amount, but the operator can choose as much as 150%. The higher the insurance, the higher their GGP rewards will be during the staking window. If a node operator has excessively low uptime (which reduces the rewards given to the pool), stakers are compensated from the insurance put up by the Node Operator. This socializes the risk of being matched with a bad operator, and minimizes any potential losses.

Subnets incentivize node operators to validate their subnet using the GGP token.

GGP token holders will have the ability to participate in the GoGoPool Protocol DAO, which allows members to propose and vote on a range of governance issues including inflation schedule of GGP, removing/replacing bad actors, smart contract upgrades, payment of community developers for future work, and rewarding outstanding members of the community (as well as other minor changes to the settings of the protocol).

### **DAO Primer**

There are two on-chain DAOs at play: OracleDAO and ProtocolDAO. These DAOs work together to keep the protocol running in a decentralized and community owned way.

Because of the open community orientation of this protocol, no platform fees will be charged. Instead, all rewards will be distributed to members of the ProtocolDAO, and losses due to bad behaviour socialized amongst members. This way all members are guaranteed the maximum possible rewards.

#### **OracleDAO**

The OracleDAO is made up of 10-20 outstanding members of the Avalanche community, and maintains a few important functions for the GoGoPool protocol:

1. Check the performance of the pool daily, and calculate the exchange rate for gAVAX and AVAX
2. (Short term) While smart contract P-Chain withdrawals/deposits are not implemented in Avalanche, the OracleDAO, ProtocolDAO, and Node Operators share ownership over sets of multisig P-Chain wallets so that staking may be initiated and rewards distributed.
3. If no node operators are present and the amount of unstaked AVAX in the deposit pool is over a decided upon threshold, OracleDAO members may form pools with their own hardware
4. Further the GGP community and protocol in the wider Avalanche community

To join the OracleDAO, members must put up a sizable sum of GGP tokens as their stake of good faith.

If the majority of members vote that a member of the DAO is not fulfilling their duties appropriately, their stake is burned and the member is kicked/replaced. Stakes must be refreshed at a decided upon time interval.

To incentivize good behaviour, 10% of inflationary GGP is paid out to the DAO.

#### **ProtocolDAO**

Our goal is to have every component of the protocol be configurable by the ProtocolDAO. Anyone with a GGP token has the ability to partake in the ProtocolDAO, proposing and voting on new items. Members of this DAO will be responsible for pushing the limits on what DAO members can and will do, and set the standard for other web3 projects.

The ProtocolDAO will maintain a treasury to pay for security audits and reward community/developer contributions.

Some of the governance factors the ProtocolDAO members have influence over are listed below:

* Depositing funds into the treasury wallet.
* The GGP token inflation schedule and rate. At genesis, there will be 5% inflation per year for 2 years.
* GGP reward distribution between Node Operators and DAOs.
* Configure min/max staking amounts, enabling/disabling registration, etc.
* Proposing and choosing a new name concluding DAO launch.
* Proposing and choosing a donation or charitable cause to donate a percentage of AVAX/GGP rewards to. At genesis, the percentage will be 1% annually.
* The signing and minting of the whitepaper, as NFTs for each member.
* Blacklisting or whitelisting subnets.

## **Enabling Subnets & Subnet Compatibility**

Avalanche is built to be the L0 other L1’s build themselves on. In other terms, Avalanche has the potential to be the ultimate “Layer 0” solution that any other Layer 1 chain builds on top of.

The only requirement is that validators of each Layer 1 solution also be a validator for the default subnet, which is the main Avalanche network. Validators can validate any arbitrary number of subnets.

At the time of writing, the minimum staking amount is 2000 AVAX, which is roughly $183k USD. It is cost prohibitive for a subnet to start building on top of Avalanche, as they need to bear the cost of running validators for their own net, as well as the 2000 AVAX per node to validate the Primary Network.

With GoGoPool, any subnet can incentivize hardware operators in the pool to validate the subnet’s chain. This lets hardware operators earn more money, while getting the subnet access to validators in a much cheaper way rather than providing their own hardware + staking funds to validate the Avalanche Primary Network.

Subnets that have specific hardware or validator requirements will be able to select node operators based on different attributes that fit the requirements of the subnet. For example, a subnet will be able to incentivize node operators that are US citizens (if that were a requirement for the subnet).

For subnets that want to be a closed system, we also intend to make GoGoPool a viable staking protocol for use on their blockchain - allowing a subnet to run a pool on their own network, while taking advantage of minimizing the AVAX staking cost by being matched with funds from the protocol’s main pool. This way, subnets can maintain control over the hardware requirements if required but still be matched with AVAX from the protocol.

Subnets can add their own validator nodes to the pool as well, and earn rewards by validating other subnets.

That way, any L1 that decides to build on Avalanche’s L0 will be able to take advantage of both the Avalanche ecosystem and GoGoPool’s open protocol as building blocks for their own purposes.

## Licensing

To further the general web3 ecosystem, all code will be GPLv3 licensed.

## **Acknowledgements**

* Rocketpool, for being the first to create an open, decentralized staking protocol.
* Ava Labs, for creating a flexible, green and fast L0 and L1 solution.
* The Multisig Labs team, for building the dream.
* The Ethereum Foundation and Bitcoin for laying the first pieces of a foundation for web3.
