# One-Click Launcher

### Minipool Streamliner Contract Documentation

The Minipool Streamliner is designed to streamline the process of participating in our staking protocol. It automates various processes, integrating with Trader Joe, ooNodz, and our native contracts for a seamless one-click solution.

**Key Functions and Workflow**

1. **Token Swaps using Trader Joe's LBRouter**:
   * The contract starts by swapping AVAX for GGP (our native token) using the LBRouter from Trader Joe.
   * It also swaps AVAX for USDC, necessary for interacting with ooNodz, which only accepts USDC for payment.
2. **Staking GGP on Behalf of the User**:
   * Once GGP is obtained through the swap, the contract stakes these tokens on behalf of the user in our staking system. This step is crucial for participating in our protocol.
3. **Node Setup with ooNodz**:
   * With USDC in hand, the contract communicates with ooNodz to set up an Avalanche node. This process includes sending USDC to ooNodz and receiving a NodeID in return. The NodeID is essential for creating a minipool.
4. **Minipool Creation**:
   * With the GGP staked and a NodeID acquired, the contract then proceeds to the final and critical step of creating a minipool in our protocol. This is the entry point for users to begin earning rewards.

**Contract's Additional Features and Safeguards**

* **Mismatched Funds Handling**:
  * The contract includes a check to ensure that the amount of AVAX sent matches the sum required for minipool creation, GGP purchase, and node rental. If the amounts don't match, the contract reverts the transaction.
* **Swap Failure Handling**:
  * If the token swap (AVAX to GGP or AVAX to USDC) fails or doesn't meet the minimum output requirement, the contract reverts the transaction, safeguarding users from unfavorable swaps.
* **Refunding Unused USDC**:
  * In cases where there are leftover USDC funds after node setup, the contract ensures these are refunded back to the user.
* **Event Emission**:
  * The contract emits events for key actions like the creation of a new streamlined minipool and refunds of USDC, aiding in transparency and tracking.

**Conclusion**

The Minipool Streamliner contract represents a significant leap in user convenience and efficiency. By automating critical steps of swapping tokens, staking, node setup, and minipool creation, it significantly lowers the barrier to entry for users and enhances their experience in our staking ecosystem
