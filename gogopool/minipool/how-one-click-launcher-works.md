---
description: >-
  A guide on our One-Click Launcher that simplifies the process of starting a
  Minipool.
---

# 🚀 How One-Click Launcher Works

The **One-Click Minipool Launcher** simplifies the process of becoming a validator on the Avalanche network, automating several key steps in a single, streamlined transaction thanks to the **Minipool Streamliner Contract**. This page explains how the launcher works and what users can expect when they choose to participate using this method.

### **Key Functions and Workflow**

1. **Initial AVAX Payment**:
   * Users start by depositing `AVAX`, which covers all necessary transactions for setting up a Minipool. This includes purchasing `GGP` for staking, acquiring `USDC` for operational fees, and contributing 1000 `AVAX` to the Minipool.
2. **Token Swaps using Trader Joe's LBRouter**:
   * The contract starts by swapping `AVAX` for `GGP` (GoGoPool’s native token) using the `LBRouter` from Trader Joe.
   * It also swaps `AVAX` for `USDC`, which is necessary for interacting with ooNodz, which only accepts `USDC` for payment.
3. **Staking GGP on Behalf of the User**:
   * Once `GGP` is obtained through the swap, the contract stakes these tokens on behalf of the user in GoGoPool’s staking system. This step is crucial for participating in GoGoPool.
4. **Node Setup with ooNodz**:
   * With `USDC` in hand, the contract communicates with ooNodz to set up an Avalanche node. This process includes sending `USDC` to ooNodz and receiving a NodeID in return. The NodeID is essential for creating a minipool.
5. **Minipool Creation**:
   * With the `GGP` staked and a NodeID acquired, the contract then proceeds to the final and critical step of creating a minipool in GoGoPool. This is the entry point for users to begin earning rewards.

### **Contract's Additional Features and Safeguards**

* **Mismatched Funds Handling**:
  * The contract includes a check to ensure that the amount of `AVAX` sent matches the sum required for minipool creation, `GGP` purchase, and node rental. If the amounts don't match, the contract reverts the transaction.
* **Swap Failure Handling**:
  * If the token swap (`AVAX` to `GGP` or `AVAX` to `USDC`) fails or doesn't meet the minimum output requirement, the contract reverts the transaction, safeguarding users from unfavorable swaps.
* **Refunding Unused USDC**:
  * In cases where there are leftover `USDC` funds after node setup, the contract ensures these are refunded back to the user.
* **Event Emission**:
  * The contract emits events for key actions like the creation of a new streamlined minipool and refunds of `USDC`, aiding in transparency and tracking.

#### **Conclusion**

The **Minipool Streamliner** contract represents a significant leap in user convenience and efficiency. By automating critical steps of swapping tokens, staking, node setup, and minipool creation, it significantly lowers the barrier to entry for users and enhances their experience in our staking ecosystem.
