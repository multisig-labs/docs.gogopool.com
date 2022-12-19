# Minipool Design Docs

Each minipool (MP) is equivalent to an Avalanche validator with a nodeID

## Minipool Status Descriptions

MP will have a status field, represented as an int (enum in solidity)

### Prelaunch

- Minipool (MP) is created in Storage.sol Key-Value data structure
- Node Operator (NodeOp) has deposited 1K AVAX and specified duration and Avalanche NodeID. Their MP is collateralized by atleast 10% with staked GGP.
- Can be moved to status `Canceled` by the Owner of the node after a 5 day waiting period and all AVAX returned.
- MP is now in a queue, and awaits getting matched with liquid staking funds.

### Launched

- Minipool is now **locked** and cannot be canceled by owner.
- Rialto withdraws 2K AVAX from vault to stake it on Avalanche P-chain and register the node as a validator

### Staking

- Minipool is now **locked** for the duration of the validation period.
- Nothing will happen until the duration is over and validation has ended.
- Rialto will Export/Import 2K AVAX plus any rewards back to MinipoolManager.sol.
- MinipoolManager.sol will handle all funds distribution to liq staking users, GGP slashing, etc, then set status to `Withdrawable`.

### Withdrawable

- Minipool is now available for node operator funds to be withdrawn. Node operator **cannot** create a new validation with us for this nodeID until they have withdrawn all funds.
- Once withdrawal happens, status is changed to `Finished`.

### Finished

- Minipool is finished, all funds withdrawn.
- Node operator can now submit another validation request with us for this nodeID. We will replace all the data from the last validation with new data for this validation. A minipool doesnt have its own `id` we always use nodeID as a primary key.

### Canceled

- If a MP is canceled it is set to this status. Can be resubmitted.
- A minipool can only be canceled by the owner after a 5 day waiting period. This is to prevent griefing.
