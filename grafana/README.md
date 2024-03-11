---
description: The math behind the numbers.
---

# 📐 Analytics Explained

[GoGoPool Analytics dashboards](https://flipsidecrypto.xyz/GoGoPool/-GGP-protocol-stats-PitGzK) provide a clear and brief understanding of GoGoPool's key metrics.

It presents consolidated data from [Flipside](https://flipsidecrypto.xyz/GoGoPool/-GGP-protocol-stats-PitGzK)'s analytical platform, enabling a comprehensive understanding of GoGoPool's operational metrics, including liquid staking performance and minipool growth, contributing to the decentralization of the Avalanche network.

Each section breaks down complex data into accessible insights across four critical areas:&#x20;

1. [Total Deposits](./#total-deposits-dashboard)
2. [ggAVAX](./#ggavax-dashboard)
3. [Minipools](./#minipools-dashboard)
4. [GGP](./#ggp-dashboard)

## Total Deposits Dashboard

This dashboard presents the total amount of `AVAX` deposited into the GoGoPool protocol.

### Key Metrics

#### **`AVAX` on the Liquid Staking Side**

Displays the total amount of `AVAX` contributed to liquid staking through GoGoPool, offering users the yield on validating while maintaining access to a liquid token `ggAVAX`.

#### **`AVAX` on the Minipool Side**

Represents the amount of `AVAX` contributed directly to minipools, which are validators funded via an equal mix of `AVAX` contributed from both the liquid stakers and Minipool operators.

#### **Total `AVAX` in Protocol**

Demonstrates summation of the total `AVAX` held within the entire GoGoPool protocol, combining liquid staking and minipool balances.

### Growth Metrics

#### **90-day Growth in Liquid Staked `AVAX`**

Indicates the growth rate of the total \`AVAX\` deposits in \`ggAVAX\` liquid staking over the last 90 days.

#### **90-day Growth in Minipool `AVAX`**

Highlights the growth rate of the total \`AVAX\` deposits in minipools over the last 90 days.

#### **90-day Growth in Total `AVAX`**

Displays the total percentage growth of all `AVAX` within GoGoPool, including both liquid staking and minipools over the last 90 days.

### Protocol TVL (Total Value Locked)

Reports the current value of all `AVAX` and `GGP` staked within GoGoPool.

## ggAVAX Dashboard

This dashboard displays specific details of `AVAX` staked through the `ggAVAX` liquid staking token, tracking yield performance and associated fees.

### Total APY

Current estimated percentage return on all staked `AVAX`, covering various yields and costs that are explained in the following sections.

$$\text{Total APY} = \text{Base Validation APY} + \text{MEV APY} - \text{Protocol Fee} - \text{Delegation Fee} - \text{Liquidity Fee}$$

### Yield Performance

#### Base Validation Yield

The annualized yield earned from validating activities over the most recent 15-day cycle (GoGoPool Validation Cycles are 15-days). It reflects the validation yield for the latest minipool cycle, which `AVAX` stakers get to participate in on an equal basis with Minipool operators.

$$\text{Base APY} = \left( \left(1 + \frac{\text{AVAX}_{\text{Earned on Latest Minipool Cycle}}}{\text{AVAX}_\text{Base Stake on Latest Minipool Cycle}} \right)^\frac{365}{15} - 1 \right) \times 100\%$$

#### MEV Yield

The annualized yield from the last 14-day cycle attributable to Maximal Extractable Value strategies.

$$\text{MEV APY} = \left( \left(1 + \frac{\text{MEV Reward}}{\text{AVAX}_{\text{Liquid Staking 14 days ago}}} \right)^{\frac{365}{14}} - 1 \right) \times 100\%$$

### Fee Structure

#### Protocol Fee

The protocol fee is zero, emphasizing that GoGoPool does not charge protocol-level fees.

$$\text{Protocol Fee} = 0$$

#### Delegation Fee

The delegation fee is calculated based on the delegated `AVAX` rate, the possible minimum commission rate (2%) of the base return. GoGoPool's goal is to sustain a 0% delegation fee, by leveraging deposited `AVAX` to generate base and MEV yields internally instead of delegating `AVAX` to external validators.

$$\text{Delegation Fee} = \left( \frac{\text{AVAX}_\text{Sent to Delegators}}{\text{AVAX} _\text{Liquid Staking}} \times \text{Base Yield APY} \times {2\%} \right)$$

#### Liquidity Fee

Represented as an opportunity cost rather than an external fee, it is calculated based on the idle `AVAX` compared to the active staking pool, incorporating both base yield and MEV yield to present the cost of liquidity.

$$\text{Liquidity Fee} = \left( \frac{\text{AVAX}_\text{Idle}}{\text{AVAX}_\text{Liquid Staking}} \times \text{(Base Yield APY + MEV Yield APY)} \right)$$

### Exchange Rate, Volume, and Market Activity

* **`AVAX` to `ggAVAX` Exchange Rate**: Current and historical rate at which `AVAX` is converted to `ggAVAX`.
* **`ggAVAX` Volume**: A comparison of trading volumes across different exchanges.

## Minipools Dashboard

The Minipools Dashboard provides a real-time count and historical trend of active minipools, which are critical components of GoGoPool’s staking infrastructure.

### Minipools

#### Total Number of Minipools

Displays the current number of active minipools and a graph showing the change in the number of minipools over time.

#### Reward Dates

* **Rewards Cycle Start**: Marks the beginning of the reward period.
* **Reward Cycle End**: The date when the current reward cycle concludes and distribution begins.
* **Rewards Eligibility**: The date when minipools are evaluated for their current rewards eligibility.
* **Next Rewards Eligibility**: The upcoming date when minipools will be evaluated for their next rewards eligibility.

## `GGP` Dashboard

A detailed look at GoGoPool's native token, `GGP`, showcasing its price, market valuation, and staking statistics.

### Market Valuation

* **`GGP` Price**: The current trading price for `GGP`, a direct reflection of the market's valuation.
* **`GGP` FDV (Fully Diluted Valuation)**: Represents the total value of all `GGP` tokens at the current market price, assuming all are in circulation.
* **`GGP` Mcap (Market Capitalization)**: The total market value of circulating `GGP` tokens, providing a snapshot of its market size and liquidity.

### Staking Statistics

* **`GGP` Percentage Staked**: The portion of `GGP` tokens currently staked in the protocol.
* **`GGP` Staked**: The total quantity of `GGP` that has been staked and the changes in the amount of staked `GGP` over time.

### Market Activity

* **`GGP` Volume**: A comparison of trading volumes across different exchanges.

