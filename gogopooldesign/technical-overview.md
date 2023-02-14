# Technical Overview

The protocol can be split into 4 components.

- [Data Separation Upgrade mechanism](#data-separation-upgrade-mechanism)
- [Liquid Staking](#liquid-staking)
- [Minipool Creation & Validation](#minipool-creating--validation)
- [Rewards](#rewards)

## Data Separation Upgrade mechanism

The protocol is designed with the ability to have upgradable contracts without fear of losing settings or funds. The storage has two, non-upgradable parts. This part of the protocol was heavily inspired by our Ethereum counterpart’s design, [Rocketpool](https://docs.rocketpool.net/developers/usage/contracts/contracts.html#introduction).

- [Storage](https://github.com/multisig-labs/gogopool-contracts/blob/master/contracts/contract/Storage.sol) (`Storage.sol`)
- [The Vault](https://github.com/multisig-labs/gogopool-contracts/blob/master/contracts/contract/Vault.sol) (`Vault.sol`)

### Storage

Storage is responsible for all persistent storage across all contracts regardless of their version. This allows us to use it as a database of sorts, storing values based on hashed keys, and even using it to store more complex data structures (see `MinipoolManager.sol`for an example). Only contracts within the GoGoPool network can write to Storage, but anyone can read from it. The Storage contract also holds the addresses to the newest versions of our network contracts, allowing the current contracts to call one another while preventing older contracts from updating data.

### The Vault

The Vault is where funds are stored for all contracts. Storing the funds in a non-upgradable vault ensures that subsequent upgrades of the protocol do not cause a loss of funds.

## Liquid Staking

Our Liquid Staking system allows for users who lack the funds to create regular AVAX Validator nodes or GoGoPool Minipool Validators (see below) to reap rewards on their tokens. The following contracts are a part of the operation of Liquid Staking.

- [ggAVAX](https://github.com/multisig-labs/gogopool-contracts/blob/master/contracts/contract/tokens/TokenggAVAX.sol) (`TokenggAVAX.sol`)
- [Oracle](https://github.com/multisig-labs/gogopool-contracts/blob/master/contracts/contract/Oracle.sol) (`Oracle.sol`)
- [Minipool Manager](https://github.com/multisig-labs/gogopool-contracts/blob/master/contracts/contract/MinipoolManager.sol) (`MinipoolManager.sol`)

### Flow

1. Liquid stakers deposit AVAX in exchange for ggAVAX
2. When there are sufficient funds deposited and a minipool to match, AVAX is withdrawn by the minipool for staking.
3. After the staking period, AVAX used for staking and Avalanche rewards are deposited back to the ggAVAX contract.
4. Rewards are reflected in the exchange rate of ggAVAX → AVAX and are streamed over a 14 day period.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1ec3c2c8-f07f-4597-a5d7-9e35680404e6/Untitled.png)

### Liquid Stakers

Users depositing AVAX in exchange for ggAVAX.

### ggAVAX

ggAVAX is our Liquid Staking token. This token is how we will keep track of our user’s staked AVAX. The token contract also contains the proper methods allowing a user to deposit and withdraw their tokens.

### MinipoolManager

In the context of Liquid Staking, the Minipool Manager is responsible for matching our Minipool with the funds the Liquid Stakers have deposited to the network. When a Liquid Staker deposits AVAX, the AVAX sits and waits for a Minipool to come online. Once a Minipool with the proper collateral has come online, and has put forth the first half of the AVAX required to start it, funds are placed into a wallet controlled by the protocol to be staked using the new minipool hardware that has come online.

## Minipool Creating & Validation

These are the contracts for creating and managing minipools staking funds. A Minipool is what we (as well as our peers at RocketPool) use to describe a validator on our network.

The following contracts are a part of the Minipool Creation and Validation processes.

- [GGP](https://github.com/multisig-labs/gogopool-contracts/blob/master/contracts/contract/tokens/TokenGGP.sol) (`TokenGGP.sol`)
- [Staking](https://github.com/multisig-labs/gogopool-contracts/blob/master/contracts/contract/Staking.sol) (`Staking.sol`)
- [Minipool Manager](https://github.com/multisig-labs/gogopool-contracts/blob/master/contracts/contract/MinipoolManager.sol) (`MinipoolManager.sol`)

### Flow

1. Node Operator stakes GGP to collateralize the AVAX they want assigned from liquid stakers.
2. Node Operator creates a minipool by submitting their desired duration, delegation fee and AVAX assignment, along with their nodeID and 1000 AVAX.
3. Rialto records that a minipool is in queue and waits until sufficient liquid staker funds before launching the minipool as a validator with avalanche
4. After the validation period is over, Rialto returns funds to the Vault and can be withdrawn by the Node Operator. Minipool Manager determines if GGP needs to be slashed for a failed validation period.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a63f7064-47c4-4f1c-a372-0c30bdf802d7/Untitled.png)

### GGP

GGP is our Utility Token. It is used as a collateral for our Minipool Validators. When someone creates a new Minipool on our network, they have to put up 10% of their requested AVAX as a collateral in GGP. For example, if they are borrowing 1000 AVAX from liquid stakers, they will have to put up 1000 AVAX \* 0.1 GGP in order to stake on our network. If the validator is failing at their duties, their GGP will be slashed and used to compensate the loss to our Liquid Stakers.

### Staking

This contract contains all the code required to update the AVAX staked and assigned, GGP staked and rewarded, and determine a GGP → AVAX collateralization ratio.

### Minipool Manager

For the context of Minipools, the Minipool manager handles creating minipools, as well as containing the functions called by our Oracle to start and end validation and reward payout.

On creation, a minipool is expected to have the required GGP Collateral as well as the proper amount of AVAX deposited to the contract. After depositing the GGP to the staking contract, the `createMinipool` function should be called along with the proper amount of AVAX for staking and a time frame for staking. After that is complete, Rialto (the Oracle) handles creating a threshold signature wallet and staking the AVAX on the network.

## Rewards

The rewards part of the protocol is responsible for calculating and distributing rewards across our minipool operators. The following contracts are a part of the rewards system.

- [Rewards Pool](https://github.com/multisig-labs/gogopool-contracts/blob/master/contracts/contract/RewardsPool.sol) (`RewardsPool.sol`)
- [Claim Node Operator](https://github.com/multisig-labs/gogopool-contracts/blob/master/contracts/contract/ClaimNodeOp.sol) (`ClaimNodeOp.sol`)

Reward are also distributed to Multisig operators and the ProtocolDAO.

### Flow

1. When a node operator creates a minipool they become eligible for GGP rewards.
2. Every rewards period tokens are inflated and distributed amongst NodeOperators, Multisigs and the ProtocolDAO
3. For Node Operators, the Rialto multisig will loop over all GGP stakers, determining eligibility based on their minipool creation time.
4. If eligible the amount of rewards earmarked for that node operator is increased in the Staking contract.
5. Finally Node Operators can claim and or restake any amount of their GGP Rewards.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8f8a18d2-470c-4796-86d9-5d1e04a01de0/Untitled.png)

### Rewards Pool

The rewards are initiated periodically by the Oracle. This calculates the amount of inflation of GGP, then calculates the amount of rewards to be distributed to node operators, multisigs and the ProtocolDAO.

### Claim Node Op

This contract contains the function that gets executed when a Node Operator wants to withdraw their funds. They also have the option to only withdraw the rewards they earned, keeping their required collateral in the network to allow for a new staking cycle.
