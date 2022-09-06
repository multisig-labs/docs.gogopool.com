# Minipool Design Docs
Each minipool (MP) is equivalent to an Avalanche validator with a nodeID

## Minipool Status Descriptions
MP will have a status field, represented as an int (enum in solidity)

### Initialised
- Minipool (MP) is created in Storage.sol Key-Value data structure
- Node Operator (NO) has deposited 1K AVAX and specified duration and Avalanche NodeID
- Can be moved to status `Canceled` by NO and all funds returned
- MP is now in a queue, and awaits enough liquid staker funds (how that works is TBD)
- Once enough funds are assigned to MP, status is moved (by who?) to `Prelaunch`

### Prelaunch
- MP is now **locked** and cannot be canceled by owner
- Should not be in this state long, it's just waiting for Rialto to pick it up and do
	- Withdraw 2K AVAX from vault to TSS C-chain address
	- Export/Import to P-Chain
	- Issue validator tx with nodeID and duration
- Probably need a way for Rialto to cancel it from this state for whatever reason

### Staking
- MP is now **locked** for the duration of the validation period.
- Nothing will happen until Rialto notices the duration is over and validation has ended. Rialto will do:
	- Export/Import 2K AVAX plus any rewards to C-chain TSS addr
	- Deposit all AVAX to GGP Vault
	- Call a `MinipoolManager.finished()` method 
- MinipoolManager.sol will handle all funds distribution to liq staking users, slashing NO, etc, then set status to `Withdrawable`

### Withdrawable
- MP is now available for NO funds to be withdrawn. NO **cannot** create a new validation with us for this nodeID until they have withdrawn all funds.
- Once withdrawal happens, status is changed to `Finished`
- If owner does not withdraw within a time frame, DAO can proactively send funds to the owner and finish.

### FInished
- MP is finished, all funds withdrawn.
- NO can now submit another validation request with us for this nodeID. We will replace all the data from the last validation with new data for this validation. A minipool doesnt have its own `id` we always use nodeID as a primary key.

### Canceled
- If a MP is canceled it is set to this status. Can be resubmitted.