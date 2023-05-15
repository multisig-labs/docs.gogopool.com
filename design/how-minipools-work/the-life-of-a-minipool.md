# The Life of a Minipool

1. The minipool gets created by the node operator.&#x20;
2. The minipool is put in a queue to be matched with liquid staking funds
3. The OracleDAO transfers 2000 AVAX (1000 AVAX from the deposit pool and 1000 AVAX from the node operator) from the C-chain to the P-chain to be staked.
4. The OracleDAO registers the minipool with Avalanche as a validator for 15 days and stakes the joint 2000 AVAX.
5. At the end of 15 days, the OracleDAO transfers the funds back to the C-chain.
6. The liquid staking funds (1000 AVAX) and their accompanying rewards are then deposited back into the deposit pool.
7. If the minipool has more time on its duration, then the protocol will recreate the minipool for another 15-day cycle. The recreated minipool will utilize the rewards that the first cycle earned, to compound long-term gains.
8. The original funds from the deposit pool from #6 are withdrawn again and pooled together with the mirrored amount from the node operator's funds and their rewards.
9. The OracleDAO once again transfers the joint funds (more than 2000 AVAX this time) from the C-chain to the P-chain to stake and registers the minipool as a validator for 15 days. This process will repeat for the full duration of the minipool.
10. Once the full duration of the minipool has been fulfilled, the node operator will be able to withdraw their funds and rewards.

Additionally, a GGP rewards cycle is underway throughout this process, enabling node operators to earn rewards on their staked GGP. More information can be found [here](ggp-rewards.md).
