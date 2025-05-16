---
description: Understand the various statuses a Minipool can have within our system.
---

# 🚦 Minipool Statuses

## Minipool Status Descriptions

Each Minipool has a status field, which you can see on the [dashboard](https://app.gogopool.com/dashboard/).

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Minipool Dashboard</p></figcaption></figure>

Details of the possible status information are explained below.

### **Prelaunch (0)**

* Minipool is created in [Storage.sol](https://github.com/multisig-labs/gogopool/blob/master/contracts/contract/Storage.sol) Key-Value data structure
* The minipool operator has deposited 1000 `AVAX`, specified duration, and Avalanche Node ID. Their minipool is collateralized by at least 10% with staked `GGP`.
* The minipool can be moved to status `Canceled` by the owner of the node after a 5-day waiting period, and all `AVAX` returned.
* The minipool is now in a queue and awaits getting matched with liquid staking funds.

### **Launched (1)**

* The minipool is now **locked** and cannot be canceled by the owner.
* **Rialto**, which handles the registering of validators with the P-chain securely and is operated by OracleDAO, withdraws 2000 `AVAX` from the vault to stake it on Avalanche P-chain and register the node as a validator.

### **Staking (2)**

* Minipool is now validating and **locked** for the duration of the validation period.
* Nothing will happen until the duration is over and validation has ended.
* **Rialto** will export/import 2000 `AVAX` plus any rewards back to `MinipoolManager.sol`.
* `MinipoolManager.sol` will handle all funds distribution to liquid staking users, `GGP` slashing, etc, then set the status to `Withdrawable`.

### **Withdrawable (3)**

* The minipool is now available for minipool operator funds to be withdrawn. The node operator **cannot** create a new minipool with this Avalanche Node ID until they have withdrawn all `AVAX` funds (user's principal and staking rewards) for this minipool.
* Once withdrawal happens, the status is changed to `Finished`.

### **Finished (4)**

* Minipool is finished, and all `AVAX` funds have been withdrawn (user's principal and staking rewards for this node).
* The minipool operator can now submit another validation request with GoGoPool for this Avalanche Node ID. GoGoPool replaces all the data from the last validation with new data for this validation.

### **Canceled (5)**

* If a minipool is canceled, it is set to this status. Minipools in this status can be resubmitted for operation.
* A minipool can be canceled instantly by its owner, with no waiting period required.

### **Error (6)**

* If a minipool is set to this status, it indicates a failure in the process, specifically during the registration phase with the Avalanche network.
* This failure typically occurs if the registration request to become a validator is rejected by Avalanche.
* Once in the `Error` status, the status will transition to `Finished` after the minipool operator initiates and completes the withdrawal of their staked funds, effectively closing the failed minipool.
