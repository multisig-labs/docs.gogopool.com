# Minipool Statuses

Each minipool is equivalent to an Avalanche validator with a NodeId

## Minipool Status Descriptions

Each Minipool has a status field

### **Prelaunch (0)**

* Minipool is created in [Storage.sol](https://github.com/multisig-labs/gogopool-contracts/blob/master/contracts/contract/Storage.sol) Key-Value data structure
* Node Operator has deposited 1K AVAX, specified a duration, and submitted their Avalanche NodeID. Their minipool is collateralized by at least 10% with staked GGP.
* Can be moved to status `Canceled` by the Owner of the node after a 5 day waiting period and all AVAX returned.
* The minipool is now in a queue, and awaits getting matched with liquid staking funds.

### **Launched (1)**

* Minipool is now **locked** and cannot be canceled by the owner.
* Rialto withdraws 2K AVAX from vault to stake it on Avalanche P-chain and register the node as a validator

### **Staking (2)**

* Minipool is now **locked** for the duration of the validation period.
* Rialto will Export/Import 2K AVAX plus any rewards back to MinipoolManager.sol.
* MinipoolManager.sol will handle all funds distribution to liquid staking pool, GGP slashing, etc, then set status to `Withdrawable`.

### **Withdrawable (3)**

* Minipool is now available for node operator funds to be withdrawn. Node operator **cannot** create a new validation with us for this NodeId until they have withdrawn all funds.
* Once withdrawal happens, the status is changed to `Finished`.

### **Finished (4)**

* Minipool is finished, all funds withdrawn.
* Node operator can now submit another validation request with us for this NodeId. We will replace all the data from the last validation with new data for this validation. A minipool doesnt have its own `id` we always use nodeID as a primary key.

### **Canceled (5)**

* If a minipool is canceled it is set to this status. Can be resubmitted.
* A minipool can only be canceled by the owner after a 5 day waiting period. This is to prevent griefing.

### Error (6)

* Minipool failed.
* The node likely failed to be registered as a validator with Avalanche.
* Will move to the status `Finished` once the node operator withdraws their funds.
