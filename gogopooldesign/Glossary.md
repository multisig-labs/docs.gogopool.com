<dl>

**_<dt>Owner</dt>_** <dd>C-chain address creating minipools with Node IDs</dd>

**_<dt>LiquidStaker</dt>_** <dd>User who deposits AVAX in exchange for ggAVAX. The ggAVAX <-> AVAX exchange rate will increase as Staking rewards are deposited.</dd>

**_<dt>Minipool</dt>_**<dd>A pool of AVAX created by a Node Operator. After being matched with Liquid Staker funds, Rialto will withdraw all funds to stake and become a validator under the Node Operator's Node ID on Avalanche's P-chian.</dd>

**_<dt>Node Operator</dt>_** <dd>An owner of a Minipool controlling hardware. They deposit half of the AVAX required to validate.</dd>

**_<dt>Protocol DAO</dt>_** <dd>Place where Protocol settings are stored. Not a DAO yet. Probably more aptly named Protocol Settings.</dd>

**_<dt>Multisig</dt>_** <dd>A threshold multisig bridge between the C-Chain and the P-Chain. Internally referred to as Rialto.</dd>

**_<dt>Rialto</dt>_** <dd>Threshold multisig bridge for moving funds between C-Chain and P-Chain. Calls to contracts to stake & process Minipools, start Rewards cycles, distribute GGP Rewards, etc.</dd>

**_<dt>Token GGAVAX</dt>_** <dd>Liquid Staking token. Represents staked AVAX in the protocol.</dd>

**_<dt>Token GGP</dt>_** <dd>Inflationary Protocol Token. Inflated tokens are used as rewards for Node Operators, the Protocol DAO and Rialto multisigs. Used as collateral for Minipools.</dd>

**_<dt>Ocyticus</dt>_** <dd>Contract to allow disabling all Multisigs and pausing other network contracts.</dd>

</dl>

## Minipool Statuses

**_<dt>PreLaunch</dt>_** <dd>Created with Node Operator AVAX and awaiting match with Liquid Staker funds and launch by Rialto.</dd>

**_<dt>Launched</dt>_** <dd>Rialto has claimed the funds and will send the validation transaction.</dd>

**_<dt>Staking</dt>_** <dd>The minipool's corresponding Node is staking and validating on Avalanche's P-chain.</dd>

**_<dt>Withdrawable</dt>_** <dd>Staking and validation period is finished and all funds & rewards have been moved back to C-chain, and the Owner can claim those funds.</dd>

**_<dt>Finished</dt>_** <dd>All funds for the Minipool have been withdrawn from the protocol.</dd>

**_<dt>Cancelled</dt>_** <dd>Minipool has been cancelled before ever starting validation.</dd>

**_<dt>Error</dt>_** <dd>An error has occurred in one of the steps.</dd>
