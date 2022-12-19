---
description: A new type of token that allows for distributed shares of a token vault.
---

# ggAVAX via ERC4626

## What is it?

- New Token type based on ERC-20
- Allows users to pool native tokens into the vault and own "shares".
- Those shares can be redeemed for the tokens.
- We then implement a strategy to maximize yield on these tokens (staking) so that our users earn interest.

## How would this work?

- Our users would deposit their AVAX into our ERC-4626 contract.
- The contract would mint them equivalent ggAVAX.
- The users can redeem ggAVAX for equivalent AVAX plus their interest.
- The deposited AVAX is then sent to our node operators to be staked for an amount of time.
- Users can then redeem their ggAVAX whenever they like.
- The contract keeps keep a bit of AVAX in reserve.
  - The rest of the AVAX will be staked.
  - When a user redeems their ggAVAX for AVAX, there has to be funds avialable that are not being staked by the minipools.
    - If there is no AVAX that has been unstaked yet, the redemtion call will fail and the user will have to come back another time.

## Implementations

- Solmates: [https://github.com/Rari-Capital/solmate/blob/main/src/mixins/ERC4626.sol](https://github.com/Rari-Capital/solmate/blob/main/src/mixins/ERC4626.sol)
