---
description: Our goals and an overview of the protocol.
---

# 📚 Litepaper

## GoGoPool: A Permissionless Staking Protocol for Subnets

### **Abstract**

GoGoPool allows Avalanche users to launch a validator node with a minimum of 1100 `AVAX` while providing instant liquidity to stakers. As a permissionless protocol, any individual, business, or project can use the protocol to stake or launch new validator nodes. Our mission is to make launching a custom blockchain as easy as possible by using Avalanche’s subnet architecture. Our vision is to enable the WordPress moment for web3 via open-source tooling, a strong community, and an open-staking protocol.

### **Introduction**

Avalanche aims to be a blazingly fast, eco-friendly, and low-fee platform that any developer may build on. They achieve this with a horizontal scaling technique called **Subnets**.

At a high level, Subnets are a group of validator nodes that come to a consensus on something (typically, a blockchain). This gives an appchain developer Avalanche’s best features for free (consensus algorithm, validator set, liquidity) and allows them to focus on creating a great experience for users without worrying about web3 infrastructure.

The problem is that Subnets are expensive to start, grow and manage. Every validator of a Subnet must also validate the Avalanche Primary Network, which requires paying 2000 `AVAX` as a minimum staking amount and managing your own hardware.

For builders that wish to experiment with building new Subnets on top of Avalanche, the cost of paying 2000 `AVAX` per node and managing all the hardware is prohibitively high. Established projects wanting to run a 5-node blockchain must pay 10,000 `AVAX` upfront before launching.

GoGoPool aims to trivialize the cost of starting, growing, and managing a Subnet with an open staking protocol that has built-in Subnet compatibility - enabling rapid experimentation with new business models and ideas in the web3 ecosystem.

### **Goals**

Our mission is to be the easiest way to launch a Subnet by lowering the cost of staking. This has 3 components:

1. Liquid staking
2. Decentralized and permissionless hardware operators
3. Subnet compatibility

* Democratize and decentralize the current state of Avalanche staking and validation
* Ensure that staking infrastructure and components are as decentralized, trustless, and scalable as possible
* Minimize deposit risk and maximize rewards by socializing staking losses and rewards across the network
* Decentralize protocol development, governance, and security using `GGP` tokenomics to create a healthy, self-sustaining community
* Maximize network rewards by allowing validators and liquid stakers to easily validate Subnets, earning Subnet rewards
* Create a scalable network that can support Avalanche’s projected Subnet growth, both now and in the long-term future
* Trivialize the cost of starting, growing, and managing a Subnet’s infrastructure
* Inspire future projects by being a model example of a web3 protocol, helping proliferate the web3 ethos in the developer community

### **Protocol Overview**

The GoGoPool protocol emphasizes trustlessness and peerlessness wherever possible, to maximize its decentralization, security, and scalability.

There are 3 main components to the protocol: the users, community (tokenomics/DAO), and custom node software.

#### **Users Primer**

There are two main users of the GoGoPool protocol, each with their own use cases.

**Minipool Operators**

They contribute their own hardware to the pool and stake 1000 `AVAX` + a minimum of 100 `AVAX` (in `GGP` tokens). Operators maintain their server infrastructure and are matched with the other 1000 `AVAX` from a deposit pool of liquid stakers. Operators charge a small operating fee (not unlike the existing delegator fee) for the use of the hardware and are also incentivized with `GGP` tokens to maintain good behavior. This enables a Minipool operator to begin staking with less `AVAX` than normally required, earning rewards both from their staked `AVAX` and through operational fees and `GGP` network rewards. Importantly, while Minipools automatically earn compound interest on `AVAX` rewards from network validation, they do not automatically restake `GGP` rewards. However, operators are free to manually restake their accrued `GGP` rewards each month to increase their staked `GGP` amount, enhancing their potential future earnings.

This triple incentive structure allows them to earn much higher rewards than only staking solo, while providing hardware to generate yield for liquid stakers, and de-risks the cost of Subnet development.

**Liquid Stakers**

Liquid Stakers are either individuals or users from an API-integrated business (e.g., a wallet). Stakers deposit `AVAX` into the deposit pool and receive `ggAVAX`, which accrues value over time based on the performance of the protocol. The deposited `AVAX` is automatically matched to node operators for staking.

Stakers are given access to instant liquidity, and are able to use `ggAVAX` in any place `AVAX` could be used. But unlike `AVAX`, `ggAVAX` steadily increases in value over time based on the performance of the pool - while not needing to trust any individual minipool operator (in contrast to the current delegator system, where trust is an explicit requirement).

Anyone can safely become a staker for as little as .01 `AVAX` - including individuals or businesses. In this way, GoGoPool opens up the entire `AVAX` economy by providing much needed liquidity to stakers and DeFi apps in a trustless manner.

GoGoPool uses a mix of smart contracts and DAOs to achieve this level of decentralization despite technical challenges that prevent a pure, trustless solution.

#### **Tokenomics Primer**

There is much room for innovation in community-driven organizations, and GoGoPool plans to be at the forefront.

We have two tokens: `ggAVAX` (liquid staking token described above) and `GGP` (protocol token used for DAO governance, rewards, insurance, and incentivizing long-term behavior).

**ggAVAX**

When a user deposits `AVAX` into the deposit pool, they receive a synthetic derivative token called `ggAVAX`.

`ggAVAX` represents a staker’s deposit plus the rewards it gains over time. This token is considered liquid and can be used like `AVAX` - users can hold it to accrue staking rewards, sell it, or use it in DeFi to earn additional yield. If there is floating `AVAX` in the deposit pool, users will be able to exchange `ggAVAX` back for `AVAX` (which burns the `ggAVAX`, and draws `AVAX` from the deposit pool). Alternatively, they will have the option to list it on any exchange listing the token and exchange it for any token they would like.

**GGP**

`GGP` is an ERC20 token and serves as the protocol token for GoGoPool.

The `GGP` tokens allow Minipool Operators to launch minipools (full Avalanche Validator nodes matched with user funds) for 1000 `AVAX`.

Minipool Operators have to stake a minimum amount of `GGP` tokens to secure their assigned staking funds as insurance of good behavior. At genesis, the minimum will be 10% of their `AVAX` staked amount, but the operator can choose to stake as much as 150%. The higher their `GGP` stake, the higher their monthly `GGP` rewards will be. Minipool Operators can use these `GGP` rewards to launch new validator nodes, increasing their overall yield. In the future, Minipool Operators may restake their monthly `GGP` rewards to request `AVAX` delegation from liquid stakers onto existing minipools.

If a minipool operator has excessively low uptime and causes a loss of rewards for the protocol, stakers are compensated from the `GGP` insurance put up by the Minipool Operator. This socializes the risk of being matched with a bad operator and minimizes any potential losses. Slashed `GGP` can be sold to token holders at a discounted rate, with `AVAX` proceeds awarded to Liquid Stakers.

`GGP` token holders will have the ability to participate in the GoGoPool Protocol DAO, which allows members to propose and vote on a range of governance issues, including the inflation schedule of `GGP`, removing/replacing bad actors, smart contract upgrades, payment of community developers for future work, and rewarding outstanding members of the community (as well as other minor changes to the settings of the protocol).

#### **DAO Primer**

There are two DAOs at play: OracleDAO and ProtocolDAO. These DAOs work together to keep the protocol running in a decentralized and community-owned way.

Because of the open community orientation of this protocol, no platform fees will be charged. Instead, all rewards are maintained by the ProtocolDAO treasury, and losses due to bad behavior are socialized amongst members. This way, all members are guaranteed the maximum possible rewards.

**OracleDAO**

The OracleDAO is initially made up of the core developer team and will be decentralized over time. This DAO operates Rialto (MPC software) and maintains a few important functions for the GoGoPool protocol:

1. Facilitate cross-chain staking: Moving collected funds from the C Chain to the P Chain.
2. Facilitate distribution of staking rewards: Moving rewards from P Chain to C Chain.
3. If no minipool operators are present and the amount of unstaked `AVAX` in the deposit pool is over a decided upon threshold, OracleDAO members may form pools with their own hardware.
4. Serve as an initial price oracle to smart contracts.
5. Further the `GGP` community and protocol in the wider Avalanche community.

To join the OracleDAO, members must stake a sizable sum of `GGP` tokens.

If the majority of members vote that a member of the DAO is not fulfilling their duties appropriately, their stake is burned, and the member is kicked/replaced. Stakes must be refreshed at a decided-upon time interval.

To incentivize good behavior, 10% of the reward `GGP` is paid out to the DAO.

**ProtocolDAO**

Our goal is to have every component of the protocol be configurable by the ProtocolDAO. Anyone with a GGP token has the ability to partake in the ProtocolDAO, proposing and voting on new items. Members of this DAO will be responsible for pushing the limits on what DAO members can and will do and setting the standard for other web3 projects.

The ProtocolDAO will maintain a treasury to pay for security audits and reward community/developer contributions.

Some of the governance factors the ProtocolDAO members have influence over are listed below:

* Depositing funds into the treasury wallet.
* The `GGP` token inflation schedule and rate. At genesis, there will be 0% inflation for 4 years, at which point the DAO can contemplate adding a 2-5% inflation rate to be used as a reward.
* GGP reward distribution between Minipool Operators and DAOs.
* Configure min/max staking amounts, enabling/disabling registration, etc.
* Decide on liquidity mining and bootstrap reward programs
* Proposing and choosing a donation or charitable cause to donate a percentage of AVAX/GGP rewards to. At genesis, the percentage will be 1% annually.
* Blacklisting / whitelisting Subnets.

### **Enabling Subnets & Subnet Compatibility**

Validators of a Subnet must also be a validator for the Avalanche Primary Network. Validators can participate in any arbitrary number of Subnets.

The minimum staking amount for the Avalanche Primary Network is 2,000 `AVAX` for a single validator node and 10,000 `AVAX` for a 5-node subnet. It is cost-prohibitive for a Subnet to start building on top of Avalanche, as they need to bear the cost of running validators for their own network as well as sourcing the `AVAX` required to validate the Primary Network.

GoGoPool gives Subnet operators a way to contact and whitelist minipool operators directly to validate the Subnet. This lets minipool operators earn more yield while getting the Subnet access to validators in a much cheaper and frictionless way.

For Subnets that want to start as a closed system, GoGoPool provides a more effective way of using their AVAX by matching their funds with liquid stakers. Subnets launch non-custodial minipools, able to use the hardware for their own purposes. If this permissioned Subnet wants to explore decentralization, they have a direct path to doing so by utilizing other minipools in the protocol.

Subnets that have specific hardware or validator requirements will be able to select minipool operators based on different attributes that fit the requirements of the Subnet. For example, a Subnet will be able to incentivize minipool operators who are US citizens (if that were a requirement for the Subnet).

Subnets that join the GoGoPool DAO to have a direct say in the future of the protocol roadmap, gain access to early Subnet tooling and features, and interface with liquid stakers and Minipool operators.

### **Acknowledgments**

* The Rocketpool team, for pioneering permissionless staking protocols, before anyone was thinking about it.
* Ava Labs, for creating a flexible, green, and fast L0 and L1 solution with a focus on Developer primitives.
* The GoGoPool Dev team, for seeing and building the dream in the very early days.
* The Ethereum Foundation and Bitcoin for laying the first pieces of a foundation for web3.
