---
description: Our goals and a brief overview of the protocol.
---

# GoGoPool Litepaper

## Author

Author: Steven

Email: steven@multisiglab.org

Last Updated: 22 September 2022

## **Abstract**

GoGoPool allows Avalanche users to stake a minimum of 0.01 AVAX and operate a validator node with a minimum of 1000 AVAX, while providing instant liquidity and earning rewards for validating Subnets. As an open protocol, any individual, business, or Subnet can plug into the protocol without being charged platform fees. Our mission is to be the easiest way to stake AVAX. Our vision is to create a thriving Subnet Economy by developing open source tooling, a strong community, and an open staking protocol.

## **Introduction**

Avalanche aims to be a blazingly fast, eco friendly, and low-fee platform that any L1 may build on. They achieve this with a horizontal scaling technique called Subnets.

At a high level, Subnets are a group of validators nodes that come to consensus on something (typically, a blockchain). This gives an appchain developer Avalanche’s best features for free (consensus algorithm, validator set, liquidity) and allows them to focus on creating a great experience for users without worrying about web3 infrastructure.

The problem is that Subnets are expensive to start, grow and manage. Every validator of a Subnet must also validate the Avalanche Primary Network (which requires paying 2000 AVAX as a minimum staking amount, and managing your own hardware).

For builders that wish to experiment with building new Subnets on top of Avalanche, the cost of paying 2000 AVAX (\~37k USD) per node and managing all the hardware is prohibitively high. For established projects wanting to run a 5 node blockchain, they must pay 10,000 AVAX upfront before launching.

GoGoPool aims to trivialize the cost of starting, growing and managing a Subnet with an open staking protocol that has built in Subnet compatibility - enabling rapid experimentation with new business models and ideas in the web3 ecosystem.

## **Goals**

Our mission is to be the easiest way to stake AVAX a decentralized, trustless and peerless staking network that is easy to use for both individuals, businesses, and Subnets. This has 3 components:&#x20;

1. Liquid Staking
2. Decentralized Hardware Operators
3. Subnet Compatibility

* Democratize and decentralize the current state of Avalanche staking + validation
* Ensure that staking infrastructure and components are as decentralized, trustless and scalable as possible
* Minimize deposit risk and maximize rewards by socializing staking losses and rewards across the network
* Decentralize protocol development, governance, and security using GGP tokenomics to create a healthy self sustaining community
* Maximize network rewards by allowing hardware operators and liquid stakers to easily validate Subnets, earning Subnet rewards
* Create a scalable network that can support Avalanche’s projected Subnet growth, both now and in the long term future
* Trivialize the cost of starting, growing, and managing a Subnet’s infrastructure
* Inspire future projects by being a model example of a web3 protocol, helping proliferate the web3 ethos in the developer community

## **Protocol Overview**

The GoGoPool protocol emphasizes trustlessness and peerlessness wherever possible, to maximize its decentralization, security, and scalability.

There are 3 main components to the protocol: the users, community (tokenomics/DAO), and custom node software.

### **Users Primer**

There are two main users of the GoGoPool protocol, all with their own use cases.

#### Node Operators

Contribute their own hardware to the pool, and stake a minimum of 1000 AVAX + 100 AVAX (in GGP tokens). Operators maintain their server infrastructure, and are matched with the other 1000 AVAX from a deposit pool of stakers. Operators charge a small operating fee (not unlike the existing delegator fee) for the use of the hardware, and are also incentivized with GGP tokens to maintain good behavior. This allows a node operator to begin staking with less AVAX than is normally required, earn rewards on their staked AVAX, and earn rewards via the operating fee and GGP network rewards.

This triple incentive structure allows them to earn much higher rewards than staking solo, while providing hardware, generating yield for liquid stakers, and de risking the cost of Subnet development.

#### Liquid Stakers

Liquid Stakers are either individuals or users from an API integrated business (e.g. Steak Wallet). Stakers deposit AVAX into the deposit pool, and are instantly assigned ggAVAX (our wrapped staking token) to provide instant liquidity which accrues value over time based on the performance of the protocol. The deposited AVAX is automatically matched to node operators for staking.

Stakers are given access to instant liquidity, being able to use ggAVAX in any place AVAX could be used. But unlike AVAX, ggAVAX increases in value over time based on the performance of the pool - while not needing to trust any individual node operator (in contrast to the current delegator system, where trust is an explicit requirement).

#### Primer Summary

Anyone can safely become a staker for as little as .01 AVAX - including individuals or businesses. In this way, GoGoPool opens up the entire AVAX economy by providing much needed liquidity to stakers and DeFi apps in a trustless manner.&#x20;

GoGoPool uses a mix of smart contracts and DAOs to achieve this level of decentralization, despite technical challenges that prevent a pure trustless solution.

### **Tokenomics Primer**

There is much room for innovation in community-driven organizations, and GoGoPool plans to be on the forefront.&#x20;

\
We have two tokens: ggAVAX (liquid staking token described above), and GGP (protocol token used for DAO governance, rewards, insurance, and incentivizing long term behavior).

#### **ggAVAX**

When a user deposits AVAX into the deposit pool, they receive a synthetic derivative token called ggAVAX.&#x20;

ggAVAX represents a staker’s deposit plus the rewards it gains over time. This token is considered liquid and can be used in any way that AVAX is used. Users will be able to exchange ggAVAX back for AVAX (which burns the ggAVAX, and draws AVAX from the deposit pool). Alternatively, they will have the option to list it on any exchange listing the token and exchange it for any token they would like.

#### **GGP**

GGP is an ERC20 token, and serves as the protocol token for GoGoPool.

Node Operators have to stake a minimum amount of GGP tokens to secure their assigned staking funds as insurance of good behavior. The minimum, at genesis, will be 10% of their staked amount, but the operator can choose as much as 150%. The higher the insurance, the higher their GGP rewards will be. Node Operators may restake their monthly GGP rewards to request AVAX delegation from liquid stakers, increasing their overall AVAX + GGP yield.

If a node operator has excessively low uptime, stakers are compensated from the GGP insurance put up by the Node Operator. This socializes the risk of being matched with a bad operator, and minimizes any potential losses. Slashed GGP can be sold to token holders at a discounted rate, with AVAX proceeds awarded to Liquid Stakers.

GGP token holders will have the ability to participate in the GoGoPool Protocol DAO, which allows members to propose and vote on a range of governance issues including inflation schedule of GGP, removing/replacing bad actors, smart contract upgrades, payment of community developers for future work, and rewarding outstanding members of the community (as well as other minor changes to the settings of the protocol).

### **DAO Primer**

There are two on-chain DAOs at play: RialtoDAO and ProtocolDAO. These DAOs work together to keep the protocol running in a decentralized and community owned way.&#x20;

Because of the open community orientation of this protocol, no platform fees will be charged. Instead, all rewards will be distributed to members of the ProtocolDAO, and losses due to bad behavior socialized amongst members. This way all members are guaranteed the maximum possible rewards.&#x20;

#### **RialtoDAO**

The RialtoDAO is initially made up of the core developer team, and will be decentralized over time. This DAO operates Rialto (our MPC software) and maintains a few important functions for the GoGoPool protocol.

1. Facilitate cross chain staking (moving collected funds from C Chain to the P Chain).
2. Facilitate cross chain staking rewards (moving rewards from P Chain to C Chain).
3. If no node operators are present and the amount of unstaked AVAX in the deposit pool is over a decided upon threshold, RialtoDAO members may form pools with their own hardware.
4. Serve as an initial oracle to smart contracts.
5. Further the GGP community and protocol in the wider Avalanche community.

To join the RialtoDAO, members must stake a sizable sum of GGP tokens.

If the majority of members vote that a member of the DAO is not fulfilling their duties appropriately, their stake is burned and the member is kicked/replaced. Stakes must be refreshed at a decided upon time interval.

To incentivize good behavior, 10% of reward GGP is paid out to the DAO.

#### ProtocolDAO

Our goal is to have every component of the protocol be configurable by the ProtocolDAO. Anyone with a GGP token has the ability to partake in the ProtocolDAO, proposing and voting on new items. Members of this DAO will be responsible for pushing the limits on what DAO members can and will do, and set the standard for other web3 projects.

The ProtocolDAO will maintain a treasury to pay for security audits and reward community/developer contributions.

Some of the governance factors the ProtocolDAO members have influence over are listed below:

* Depositing funds into the treasury wallet.
* The GGP token inflation schedule and rate. At genesis, there will be 0% inflation for 4 years, at which point the DAO can contemplate adding a 2-5% inflation rate to be used as rewards.
* GGP reward distribution between Node Operators and DAOs.
* Configure min/max staking amounts, enabling/disabling registration, etc.&#x20;
* Proposing and choosing a donation or charitable cause to donate a percentage of AVAX/GGP rewards to. At genesis, the percentage will be 1% annually.
* Blacklisting / whitelisting Subnets.

## **Enabling Subnets & Subnet Compatibility**

Validators of each Subnet must also be a validator for the default Subnet, which is the main Avalanche network. Validators can participate in any arbitrary number of Subnets.&#x20;

At the time of writing, the minimum staking amount is 2000 AVAX, which is roughly $37k USD. It is cost prohibitive for a Subnet to start building on top of Avalanche, as they need to bear the cost of running validators for their own net, as well as the 2000 AVAX per node to validate the Primary Network.&#x20;

With GoGoPool, any Subnet can incentivize hardware operators in the pool to validate the Subnet’s chain. This lets hardware operators earn more money, while getting the Subnet access to validators in a much cheaper way rather than providing their own hardware + staking funds to validate the Avalanche Primary Network.&#x20;

Subnets that have specific hardware or validator requirements will be able to select node operators based on different attributes that fit the requirements of the Subnet. For example, a Subnet will be able to incentivize node operators that are US citizens (if that were a requirement for the Subnet).&#x20;

For Subnets that want to be a closed system, we also intend to make GoGoPool a viable staking protocol for use on their blockchain - allowing a Subnet to run a pool on their own network, while taking advantage of minimizing the AVAX staking cost by being matched with funds from the protocol’s main pool. This way, Subnets can maintain control over the hardware requirements if required but still be matched with AVAX from the protocol.&#x20;

Subnets can add their own validator nodes to the pool as well, and earn rewards by validating other Subnets.&#x20;

That way, any L1 that decides to build on Avalanche’s L0 will be able to take advantage of both the Avalanche ecosystem and GoGoPool’s open protocol as building blocks for their own purposes.&#x20;

## **Acknowledgements**

* Rocketpool, for being the first to create an open, decentralized staking protocol.
* Ava Labs, for creating a flexible, green and fast L0 and L1 solution.
* The GoGoPool Dev team, for building the dream.
* The Ethereum Foundation and Bitcoin for laying the first pieces of a foundation for web3.
