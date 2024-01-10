---
description: The math behind the numbers.
---

# Grafana Explained

GoGoPool contains a great deal of information that feels pretty inside baseball until you fully grasp 
the mechanics of the protocol. Much of the important protocol information we have displayed on 
[Grafana](https://multisiglabs.grafana.net/public-dashboards/4d21b06344684b8ab05ddd2828898ec8?orgId=1).
Lets go through Grafana's page number by number. 

### Protocol TVL 

Total Value Locked (TVL) is a metric for the total value of locked digital assets in the protocol, in this 
case it is a combination of the assets that are used for staking in our protocol. There are three:

1. GGP Stake
2. ggAvax Stake
3. Minipool Avax Stake

$$ \text{TVL} = GGP Stake + ggAvax Stake + Minipool Avax Stake $$

### Liquid Staking APY

This number is an estimate. The way we calculate liquid staking APY is by viewing the real performance 
of ggAvax over the course of 90 days, and multiplying by 4 to get an estimate of it's performance over 
the course of the year.

$$ \text{ggAVAX APY} = \left( \frac{\text{Current Exchange} - \text{90 days ago Exchange}}{\text{90 days ago Exchange}} \right) \times 100\% \times 4\ $$

### NodeOp APR

This number is an estimate. Node Operator APR is determined by the rewards gained by a minipool for 
a one month cycle multiplied by 12 to get an estimate for a year. 

$$ \text{APR} = \left( \frac{{ggpRewardsAsAvax} + {AvaxRewards}}{{AvaxStaked + ggpStakedAsAvax}} \right) \times 100\% \times 12 $$

*The number displayed on Grafana is currently inaccurate*

### Available Minipools

In order for minipools to be available, there must be 1000 available staking avax. For every 
1000 staking Avax, 1 new minipool can be made. Therefore:

$$ \text{Available Minipools} = \left(\frac\text{Available Staking Avax}{1000} \right) $$

### Active Minipools 

Minipools can be in 7 distinct states:

- Cancelled
- Error
- Finished
- Withdrawable
- Launched
- Prelaunch
- Staking

These states are mutually exclusive. When a minipool is made it first is in `Prelaunch` state, where 
the user has created a minipool but their funds have not yet been matched. When their funds have been matched 
they are placed in the `Launched` state. During this state contract calls are made to make the minipool available 
for staking. When the appropriate contract calls are confirmed, the minipool begins `Staking`. A minipool 
is considered `Active` if it is in the `Staking` state. This means the assets are locked in the minipool 
for the staking duration of the minipool which is set by the user upon creation. When a minipool is done 
staking it moves to the `Withdrawable` state until the funds are removed, where it's finally moved to `Finished`. 

#### GGP Staked
The total amount of GGP staked by users. 

#### GGP Price
The current price of the GGP Token. 

#### Reward Cycle's Explained
Reward cycles are on a 30 day timeframe. There are 4 related variables in grafana: 

- Reward Cycle Start
- Reward Cycle End
- Rewards Eligibility Cutoff Date
- Next Rewards Eligibility Date

Start and end are self explanatory. A minipool must be created before the `Rewards Eligibility Cutoff Date` 
in order to earn rewards for the 30 day cycle. If you missed the current cutoff date, our grafana page also 
displays the following cutoff date for the next 30 day cycle. 

#### ggAvax Last Rewards

ggAvax is our protocol's liquid staking token. This token accrues value by rewards from each 30 day 
reward cycle. When a rewards cycle ends some of the money that the minipool made from staking on the Avax 
network is returned to the assets pool. Just over 50% the amount made from staking on the Avax network
is given to node operators because of an included node op fee. Just under 50% is returned to the liquid 
staking pool to accrue value. 

$$ \text{Half Rewards} = \left(\frac{avaxTotalRewards}{2}\right) $$

$$ \text{Liquid Staker Reward Amount} = {Half Rewards} - \left(Half Rewards\times{Node Op Fee Percent}\right) $$
$$ \text{Node Operator Reward Amount} = {Total Rewards} - {Liquid Staker Reward Amount}  $$

*As of 01/10/2024 the node op commision fee percent is 15%. Meaning liquid 
stakers will receive 42.5% of rewards and node operators 57.5%.*



#### How ggAvax Works

ggAvax is the protocol's liquid staking token. It uses ERC-4626 which is a tokenized vault contract. 
You can think of ggAvax as shares that accrue value over time. The value increases as the asset pool 
increases in relation to the supply. Liquid staking puts Avax into the Avax Total Assets and the Avax 
Total Supply. The ratio is increased by ggAvax last rewards, when the rewards from the minipool are 
put into the assets, but not the total supply. 

|Event|Avax Total Assets|Avax Total Supply|
|----|----|----|
|Liquid Stake| + | + |
|Rewards Cycle| + |  |

In this way ggAvax will become more valuable over time due to the always decreasing ratio of supply 
to assets. 

$$ \text{ggAvax} = \frac{Avax Supply}{Avax Assets} $$

