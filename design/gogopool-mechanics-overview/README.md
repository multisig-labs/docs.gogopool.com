---
description: Overview on how GoGoPool works
---

# GoGoPool Mechanics Overview

GoGoPool core mechanics revolve around the concept of a minipool. This term was originally coined by RocketPool, which GoGoPool is based on.  A GoGoPool minipool represents a validator that was funded via AVAX contributed from liquid stakers via the deposit pool and AVAX contributed from node operators during their registration with GoGoPool.

To become a validator on Avalanche, the current requirement is 2000 AVAX. With GoGoPool's minipool design, the upfront cost for node operators drops to 1100 AVAX. Learn more about how minipools work here (coming soon).

The 2000 AVAX requirement is met through sourcing 1000 AVAX from GoGoPool's liquid stakers. Learn more about liquid staking works [here](../how-liquid-staking-works/).

To ensure good behavior and collateralize the AVAX the node operators are borrowing from the liquid staker's deposit pool, node operators stake at least 100 AVAX worth of GGP. Because they are staking GGP, they also have an opportunity to earn monthly GGP rewards. Learn more about the GGP rewards cycle here (coming soon).\
\
If a validator fails to get rewarded by Avalanche, then the node operator's staked GGP gets slashed to make up for the liquid staker's loss of rewards.\
\
The protocol operates with two DAOs. The ProtocolDAO, which is tasked with the longterm sustainability fo the protocol and is goverened with the GGP token. And the OracleDAO which is tasked with handling offchian interactions. Learn more about the two DAOs here (coming soon).
