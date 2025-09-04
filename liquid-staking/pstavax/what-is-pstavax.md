# What is pstAVAX

**`pstAVAX`** (_Principal Staked AVAX_) is an [ERC-20](https://eips.ethereum.org/EIPS/eip-20) token designed for users who want to support the Hypha ecosystem's growth in exchange for **direct incentives from Hypha**.

It represents a user's principal deposit at a fixed **1-to-1 ratio**. When you deposit 1 `AVAX` (or `WAVAX`), you receive exactly 1 `pstAVAX`. Under the hood, your deposited `AVAX` is converted into `stAVAX` and held by the `pstAVAX` contract, where it generates yield for the ecosystem.

The most important feature of `pstAVAX` is that holders **do not receive this yield**. Instead, the yield that would have been earned is automatically stripped and used to benefit all `stAVAX` holders. In return, `pstAVAX` holders become eligible for a separate reward system, such as airdrops and other direct incentives from Hypha.

{% hint style="success" %}
## Alignment Plugins

`pstAVAX` is the first of Hypha's _alignment plugins_, a new type of tool that allows protocols to build innovative incentive structures on top of staked assets. This means other L1s can use this same model to create their own version (i.e., `xyzAVAX`). In exchange for offering their own project's tokens, airdrop points, or other unique perks to depositors, these L1s can use the resulting staking yield to bootstrap liquidity, generate protocol revenue, or fund their operation.
{% endhint %}

You can redeem your `pstAVAX` to get your initial `AVAX` deposit back by withdrawing it directly as `AVAX`. This process uses the standard [Withdrawal Queue](../stavax/unstaking-and-the-withdrawal-queue.md), which includes a 15-day cooldown period. The final amount of `AVAX` you receive will be equal to your initial deposit.
