---
description: >-
  ERC4626 is a new type of token that allows for distributed shares of a token
  vault.
---

# ggAVAX via ERC4626

## What is it?

* New Token type based on ERC-20
* Allows users to pool native tokens into the vault and own "shares".
* Those shares can be redeemed for the tokens.
* Protocols then implement a strategy to maximize yield on these tokens (staking) so that its users earn interest.

## How does this work for GoGoPool?

* Users deposit their AVAX into our ERC-4626 contract, known as TokenggAVAX.
* The contract mints them equivalent ggAVAX.
* Users can redeem ggAVAX for equivalent AVAX plus their interest.
* The deposited AVAX is then sent to our minipools to be staked for an amount of time.
* Users can then redeem their ggAVAX whenever they like, if there is floating AVAX available.

## Inspiration

* Solmates: [https://github.com/Rari-Capital/solmate/blob/main/src/mixins/ERC4626.sol](https://github.com/Rari-Capital/solmate/blob/main/src/mixins/ERC4626.sol)
