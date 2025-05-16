# ⛓️ How Liquid Staking Works

Liquid staking transforms the native staking process into a more flexible and accessible model.

## Liquid Staking Work Flow

GoGoPool introduces a unique mechanism known as **Minipools** to facilitate liquid staking and validator operations on the Avalanche network. Here's how it works in detail:

1. **Staking Deposit**: When users stake `AVAX` in GoGoPool, their assets are directed into the deposit pool, essentially serving as the reserve for creating new validators.
2. **Token Issuance**: In exchange for the staked `AVAX`, users receive `ggAVAX`, the liquid staking token. This token represents the user's staked AVAX plus any accruing rewards, including base validator rewards and good MEV rewards.
3. **Validator Matching Through Minipools**: The deposited AVAX is pooled together and used to match with users who want to become a validator for Avalanche's primary network.
4. **Funds Transfer and Activation**: Utilizing advanced multisig technology, GoGoPool transfers these combined funds from the C-chain (Contract Chain) to the P-chain (Platform Chain) and officially registers the Minipool as a validator on the Avalanche network.
5. **Validation Period**: Each Minipool enters a validation period, commonly lasting about 15 days, during which it participates in network consensus and earns rewards.
6. **Reward Distribution**: Upon completing its validation cycle, the Minipool's accrued rewards, including base validation and any additional MEV rewards captured over their periods, are consolidated. These rewards, along with the original 1000 AVAX staked from the deposit pool, are transferred back to the C-chain. The combined rewards are then streamed into the rewarder, which distributes them block-by-block over the following 14-day cycle.
7. **Token Utility**: `ggAVAX`is fully liquid, meaning it can be traded, sold, or used within DeFi applications. Users can hold onto their tokens to accumulate staking rewards or utilize them for other investment opportunities.
8. **Redemption**: When users decide to redeem their `ggAVAX` for `AVAX`, they can do so based on the current value, which includes accumulated rewards. The process involves burning `ggAVAX` and returning the equivalent amount of the `AVAX` to the user.

{% hint style="info" %}
A **minipool** is essentially a full Avalanche Validator node but is uniquely supported by liquid staking funds. When a minipool is established, it combines 1000 `AVAX` from the user's deposit pool with an equivalent contribution from a minipool operator, meeting Avalanche’s 2000 `AVAX` minimum staking requirement for validator nodes.
{% endhint %}

## Redemption

At any time, users can receive the `AVAX` they deposited along with the accrued rewards in exchange for `ggAVAX` by either unstaking via GoGoPool or immediately swapping via DEXs.

* **Unstaking**: Users can directly redeem `ggAVAX` for `AVAX` through GoGoPool when they choose to. This process is subject to the availability of liquidity in the pool. GoGoPool endeavors to ensure there is adequate liquidity to allow for redemptions with low price impact. The unstaking process is straightforward and ensures users can convert their liquid staking tokens back to `AVAX` easily.
* **Immediate Swapping**: `ggAVAX` holders have the flexibility to swap their tokens for AVAX at any time without waiting, thanks to liquidity available on decentralized exchanges (DEXs). This allows for immediate access to AVAX in exchange for `ggAVAX` based on current market rates. For optimal trade execution, it's recommended to utilize a meta aggregator (i.e., [LlamaSwap](https://swap.defillama.com/?chain=avax\&from=0x0000000000000000000000000000000000000000\&to=0xa25eaf2906fa1a3a13edac9b9657108af7b703e3)), which can route trades through the most liquid pools to minimize slippage.

GoGoPool actively manages its liquidity provisions to support both unstaking and swapping processes, ensuring a seamless redemption experience.
