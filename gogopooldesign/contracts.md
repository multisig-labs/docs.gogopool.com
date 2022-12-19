# Contracts

`Storage.sol` <dd>The GoGoPool smart contract architecture is based around techniques from [RocketPool](https://github.com/rocket-pool/rocketpool). The `Storage.sol` contract is non-upgradeable, and contains generic getters/setters to access it's storage. Other contracts are "registered" with the storage contract as a "Network Contract", and can then use it to read and write typed key/value pairs. In this way, other contracts can be upgraded at will, as they contain no local storage of their own. </dd>

`Vault.sol` <dd> Non-upgradeable contract used to store AVAX/ERC20 tokens on behalf of other network contracts. Not storing value in network contracts allows them to be upgradeable.</dd>

`MultisigManager.sol` <dd>Registry of Rialto TSS (Threshold Signatures) wallets that are allowed to extract protocol funds and deploy them into yield-bearing staking transactions on the Avalanche P-chain.</dd>

`Ocyticus.sol` <dd> Protocol emergency pause feature, such that any one of a specified group of "Defenders" can pause the entire protocol should that be necessary. The Defenders will be a different set of users from Guardians, and their only permission will be the ability to call the Pause function. Only the Guardian can add and remove Defenders.</dd>

`TokenGGP.sol` <dd> Fixed-supply, non-upgradeable GGP utility token. GGP is our protocol token used to collateralize minipools and rewards Node Operators in addition to the AVAX Validation rewards.</dd>

`TokenggAVAX.sol` <dd>Upgradeable (via OpenZeppelin proxy) [ERC4626](https://eips.ethereum.org/EIPS/eip-4626) yield-bearing liquid staking token. Additionally, the [xERC4626](https://github.com/fei-protocol/ERC4626/blob/main/src/xERC4626.sol) technique is used to stream rewards to users over a set cycle period. AVAX funds from TokenggAVAX are used by Node Operators to create a full validator from their minipool.</dd>

`Base.sol`, `BaseAbstract.sol`, `BaseUpgradeable.sol` <dd> modifiers, helper methods and storage wrapper methods. `BaseAbstract` is where the implementation lives, and it’s inherited by both `Base` and `BaseUpgradeable` to be used in standard network contracts and the proxy upgradeable `TokenggAVAX` , respectively.</dd>

`ClaimNodeOp.sol`, `ClaimProtocolDAO.sol` <dd> Two contracts for claiming inflated GGP Tokens. Multisig isn’t included here as a separate contract, we instead distribute those rewards right from `RewardsPool.sol`. </dd>

`Oracle.sol` <dd> GGP price submission from Rialto oracle.</dd>

`ProtocolDAO.sol` <dd> Maintains protocol settings used across all network contracts. Currently all settings are controlled by the Guardian. In a future iteration will include a DAO mechanism for modifying settings.</dd>

`RewardsPool.sol` <dd> Handles GGP rewards cycles which includes inflation of new tokens and distribution of the tokens to the claiming contracts.</dd>

`Staking.sol` <dd> Access point for staking GGP. Also maintains information on Node Operators. GGP staked, AVAX staked, AVAX assigned, rewards eligibility time.</dd>
