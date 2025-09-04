# What is stAVAX

**`stAVAX`** (_Staked AVAX_) is a yield-bearing liquid staking token that represents your staked AVAX within the Hypha ecosystem. It is designed as an [**ERC-4626**](https://ethereum.org/en/developers/docs/standards/tokens/erc-4626/) tokenized vault, a DeFi standard that makes it highly composable and easy to integrate with other protocols.

The core purpose of `stAVAX` is to solve the liquidity problem of traditional staking. It allows you to **earn comprehensive yields** from the Avalanche network while keeping your funds liquid, meaning you can trade, lend, or use your staked position in DeFi applications without locking your `AVAX`.

### How It Works

When you stake `AVAX` into [Hypha](https://app.gogopool.com/liquid-staking/) on the C-Chain, you receive an equivalent amount of `stAVAX` based on the current exchange rate. The protocol then securely transfers these funds to Avalanche's Platform Chain (P-Chain).

On the P-Chain, your AVAX is put to work by validating the network through a group of high-performance validators. A portion of these validator nodes may also opt-in to perform MEV (Maximal Extractable Value) to capture additional profit.

By combining these strategies, the underlying pool of AVAX earns yield from multiple sources. As this yield is collected, the total assets in the vault increase, which means the value of each `stAVAX` token you hold grows over time in relation to `AVAX`. For example, you might eventually be able to redeem `1 stAVAX` for `1.2 AVAX`.

The protocol runs on continuous 15-day staking cycles. Funds are staked on the P-Chain to earn validation rewards, then transferred to the C-Chain vault at the end of each cycle. Over the following 15 days, these rewards are streamed to the stAVAX contract, automatically raising the AVAX value of all stAVAX. This creates a seamless loop where new staking begins as previous rewards are added, ensuring stAVAX steadily appreciates against AVAX.

### Key Benefits

* **Liquid Staking**: Earn staking rewards without locking up your capital.
* **DeFi Composability**: Use `stAVAX` as collateral, a liquidity pair, or in yield farming strategies across Avalanche DeFi.

