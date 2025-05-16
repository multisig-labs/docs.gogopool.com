---
description: >-
  Stake assets, purchase node licenses, and support L1 chains on Hypha's L1
  Marketplace (L1M).
icon: steak
---

# How to Stake and Support L1 Chains

This guide explains the general process for participating in L1 staking via Hypha's [L1 Marketplace (L1M)](https://l1s.gogopool.com/marketplace).

> ⚠️ **Note:** This is a _generic_ staking guide applicable to all L1s using Hypha. Some parameters (like token names, NFT availability, credit costs, and rewards) may vary _across_ different L1 chains.

## Key Concepts

### Node License NFTs

L1 projects offer **Node License NFTs** (ERC-721 tokens) during launch. These NFTs grant holders the right to run validator nodes for the chain.&#x20;

L1 projects can use node license sales to raise early funding and bootstrap validator communities. For participants, this provides an opportunity to actively support the L1 projects they believe in and gain early exposure.

NFTs are typically available during a project’s launch phase but may not be on sale at all times. You can view and purchase node licenses (if available) directly from the project’s page on the [L1 Marketplace](https://l1s.gogopool.com/marketplace).

### Node Hosting (Node-as-a-Service)

Holders of Node License NFTs can choose to host their node with Hypha by paying a **monthly USDC fee**. This managed hosting service removes technical barriers for NFT holders.

> **Bonus:** Hosting a node may qualify participants for an airdrop when the chain’s token generation event (TGE) occurs.

### Staking Credits

Staking credits are required to activate your node licenses and begin earning rewards:

* Each **active** node license consumes **1 staking credit per month**.
* If your account runs out of credits, your license will be removed from the staking contract and **will no longer earn rewards**.

> You can top up staking credits anytime from your dashboard.

## How to Participate in L1 Staking

{% stepper %}
{% step %}
### Visit the L1 Marketplace

* Navigate to the [L1 Marketplace](https://l1s.gogopool.com/marketplace)
* Browse available L1 projects on the Avalanche L1 ecosystem
{% endstep %}

{% step %}
### Connect Your Wallet

* Click **Connect Wallet** and link an EVM-compatible wallet (e.g., MetaMask, Core, Rabby)
* Ensure your wallet is connected to the **Avalanche C-Chain**
{% endstep %}

{% step %}
### Choose a Project

* Select the L1 project you want to support
* On the project page, you'll see:
  * Overview of the chain and its vision
  * Node License availability and price (if applicable)
  * Links to the whitepaper, socials, and docs
  * **Buy Node License** or **Stake** options
{% endstep %}

{% step %}
### Purchase a Node License (If Available)

If the project is selling node licenses:

* Click **Buy Node License**
* Confirm the transaction in your wallet to mint an ERC-721 license NFT

These NFTs are required to participate in staking.
{% endstep %}

{% step %}
### Stake Your Node Licenses

* Click **Stake now**&#x20;
* Select the **staking amount** (how many licenses you want to stake)&#x20;
* Select the **staking duration** - _staking is currently only available in 6-month intervals._

{% hint style="info" %}
#### :closed\_lock\_with\_key: Staking Lock-In

Once you stake, your licenses are **locked for the entire selected duration**.\
You **cannot unstake** early — so be sure you’re comfortable with the lock-in period before confirming.
{% endhint %}

* **Pay the staking cost** in USDC — _the total is based on the number of nodes and months selected._
* Click the button and follow the instructions to stake

{% hint style="info" %}
#### 💡 Batch **Processing via Vault**

To reduce gas fees and make staking easier, you’re granting permission to the **Hypha License Vault** to stake your licenses **on your behalf**. This allows you to stake multiple NFTs in one go.
{% endhint %}

<div align="center"><figure><img src="../.gitbook/assets/Purchase Staking services.png" alt="" width="375"><figcaption><p>Paying staking cost and Staking</p></figcaption></figure></div>

After your transaction is confirmed, you can view your **Staked** node licenses on the project's L1 Marketplace page.

> ⚠️ **Important:** If you run out of staking credits, your NFTs will be removed from staking automatically.
>
> 💡 **Tip:** Check the total number of months you want to stake in advance, so you can calculate how many credits to purchase accordingly.
{% endstep %}
{% endstepper %}
