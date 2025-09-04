---
hidden: true
---

# How to Earn Points & Multipliers

Points are calculated based on a simple formula and then boosted by multipliers depending on your activity.

### The Base Calculation

The foundation of the points system is: `1 AVAX of value = 1 Point per hour`

All eligible assets are measured by their **AVAX-equivalent value** to determine the **base points you earn each hour**. Multipliers are then applied on top of this base rate.

### Point-Earning Activities & Multipliers

#### Operating Minipools (1.5x - 2.5x Multiplier)

Run a Minipool to validate the Avalanche network and earn the highest multipliers in the program.

| Number of Minipools | Multiplier |
| ------------------- | ---------- |
| 1 Minipool          | 1.5x       |
| 2-4 Minipools       | 1.75x      |
| 5-9 Minipools       | 2.0x       |
| 10+ Minipools       | 2.5x       |

> **Note:** These multipliers are tiered and apply only to the points earned from your Minipool operations. For example, if you run 3 Minipools, all points from those pools receive a 1.75x multiplier.

{% hint style="success" %}
## Example Points Calculation

You operate 2 Minipools, each containing 1,000 AVAX.

* **Total AVAX Value**: `2 * 1,000 AVAX = 2,000 AVAX`
* **Base Points**: `2,000 points per hour`
* **Multiplier for 2 Minipools**: `1.75x`
* **Total Points**: `2,000 * 1.75 = 3,500 points per hour`
{% endhint %}

#### Staking GGP (1.5x Multiplier)

Stake the protocol's `GGP` token to earn a boosted rate on your stake.

* **Multiplier**: 1.5x
* **Note**: Your staked `GGP` is converted to its AVAX-equivalent value to calculate your base points before the multiplier is applied.

{% hint style="success" %}
## Example Points Calculation

You stake **10,000 GGP** and the current market rate (hypothetically) is `1 GGP = 0.1 AVAX`.

* **Total AVAX-equivalent Value**: `10,000 GGP * 0.1 = 1,000 AVAX`
* **Base Points**: `1,000 points per hour`
* **Multiplier**: `1.5x`
* **Total Points**: `1,000 * 1.5 = 1,500 points per hour`\

{% endhint %}

#### Holding stAVAX (1x Rate)

Hold Hypha's liquid staking token, `stAVAX`, to earn points.

* **Multiplier**: None (1x base rate).
* **Note**: `stAVAX` is a yield-bearing token, so its value in AVAX increases over time. Your points are calculated based on the current exchange rate, meaning you earn more points as your `stAVAX` accrues value.

{% hint style="success" %}
## Example Points Calculation

You hold 1,000 stAVAX, and the current exchange rate (hypothetically) is `1 stAVAX = 1.13 AVAX`.

* **Total AVAX-equivalent Value**: `1,000 stAVAX * 1.13 = 1,130 AVAX`
* **Base Points**: `1,130 points per hour`
* **Multiplier**: `1x`
* **Total Points**: `1,130 * 1 = 1,130 points per hour`&#x20;
{% endhint %}

#### Upcoming Integrations

Post-launch, we plan to expand the points program to include DeFi activities on major Avalanche protocols. This will allow you to earn points for actions such as providing liquidity involving our tokens.

***

### Point Calculation and Snapshots

#### Frequency

Points are calculated and awarded hourly.

#### Snapshot Mechanism

A snapshot of your wallet and on-chain positions is taken at the top of each hour.

#### Eligibility Rule

To earn points for a given hour, you must hold qualifying assets (e.g., minipools, staked GGP, stAVAX) throughout the entire period. We compare consecutive snapshots to verify this. For example, if you acquire or drop assets mid-hour, you won't earn for that interval. This prevents short-term gaming (e.g., holding for just a minute around snapshot time).

#### Data Source

All data is pulled from standardized sources like Dune, which users can query independently for verification.

***

### FAQ

#### How do I track my points?

A points dashboard will be made available soon. In the meantime, all data is public and can be verified using on-chain analytics tools such as [Dune Analytics](https://dune.com/).

#### Can I game the system?

The hourly snapshot mechanism is designed to reward consistent, long-term participation and discourage short-term holding around the snapshot time.

#### Will the rules change over time?

We may adjust multipliers or add new ways to earn points based on community feedback and the needs of the ecosystem. All changes will be announced through our official channels.

#### What are the points for?

Points measure your contribution to the Hypha ecosystem and may be redeemed for airdrops, governance perks, or other rewards.
