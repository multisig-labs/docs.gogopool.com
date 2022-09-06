---
description: A new type of token that allows for distributed shares of a token vault.
---

# ggpAVAX via ERC-4626

## What is it?

* New Token type based on ERC-20
* Allows users to pool native tokens into the vault and own "shares".
* Those shares can be redeemed for the tokens.
* We then implement a strategy to maximize yield on these tokens (staking) so that our users earn interest.

## How would this work?

* Our users would deposit their AVAX into our ERC-4626 contract.
* The contract would mint them equivalent ggpAVAX.
* The users can redeem ggpAVAX for equivalent AVAX plus their interest.
* The deposited AVAX is then sent to our node operators to be staking for an amount of time.
  * It may be a good idea to require users to wait a certain period of time before they can unstake their ggpAVAX.
* Users can then redeem their ggpAVAX whenever they like (or after a minimum hold time).
* The contract should still keep a bit of AVAX in reserve.
  * The rest of the AVAX will be staked.
  * When a user unstakes their AVAX, the reserves would be hit before any AVAX should be unstaked.
    * If there is no AVAX that has been unstaked yet, keep track of it and send the user it as soon as it becomes avaiiable.
* By default, the shareholders (the ggpAVAX holders) are the ones that pay all fees.
  * These includes standard gas fees, as well as all fees payed to have the AVAX staked.&#x20;
  * If we decide we don't want this, we will have to modify an existing implementation, which means it may need re-audit

## What we would need to do.

* Implement ggpAVAX that inherits from Solmates' ERC-4626 Implementation.
* Implement a way for the Oracle to grab AVAX and stake it via our hardware operators.
  * Make sure that a small reserve is kept.
* Implement a way for the ggpAVAX contract to request funds from the currently staked AVAX and to send the funds to the user who requested a withdrawal.
  * Some sort of waiting period so that user's can't pull out immediately?
  * Do we want to charge users the gas fees for staking and transferring between contracts?

## Implementations

* Solmates: [https://github.com/Rari-Capital/solmate/blob/main/src/mixins/ERC4626.sol](https://github.com/Rari-Capital/solmate/blob/main/src/mixins/ERC4626.sol)
* Vyper: [https://github.com/fubuloubu/ERC4626](https://github.com/fubuloubu/ERC4626)
* OpenZeppelin WIP: [https://github.com/OpenZeppelin/openzeppelin-contracts/pull/3171](https://github.com/OpenZeppelin/openzeppelin-contracts/pull/3171)&#x20;

## Sources

* [https://eips.ethereum.org/EIPS/eip-4626](https://eips.ethereum.org/EIPS/eip-4626#abstract)
* [https://github.com/ethereum/EIPs/pull/4626](https://github.com/ethereum/EIPs/pull/4626)
* [https://www.coindesk.com/layer2/2022/01/13/erc-4626-defis-newest-money-lego/](https://www.coindesk.com/layer2/2022/01/13/erc-4626-defis-newest-money-lego/)
* [https://cryptomarketpool.com/vaults-and-the-erc-4626-token-contract/](https://cryptomarketpool.com/vaults-and-the-erc-4626-token-contract/)
