# Manual Setup

To test GoGoPool on Fuji, use our [faucet](https://faucet.gogopool.com) to get test GGP.

{% hint style="info" %}
The visuals for each setup below show how to create a Minipool on Fuji. The steps are the same as on Mainnet, but the AVAX and GGP requirements are different.
{% endhint %}

## Creating a Fuji or Mainnet node

To use GoGoPool as a node operator, and earn rewards on your staked GGP, you have to have an Avalanche node. To create a node, see the [Official Avalanche guides](https://docs.avax.network/nodes). Once you have a NodeId, come back to GoGoPool to register as a validator.

## How to make a Minipool with Manual Setup

### Step 1: Register a NodeId with GoGoPool

<figure><img src="../../.gitbook/assets/gogopool_register_node.png" alt=""><figcaption><p>Place your NodeId in the input box as shown, then press next.</p></figcaption></figure>

### Step 2: Submit BLS Public Key

Enter your BLS public key and signature for verification. Further information about BLS keys, why they are needed, and how to access yours is [here](https://docs.gogopool.com/security/avalanche-bls-keys#how-do-i-acquire-my-nodes-bls-keys).

<figure><img src="../../.gitbook/assets/gogopool_blsKeys.png" alt=""></figure>

### Step 3: Approve and Deposit GGP

Your wallet provider will prompt you to approve and transfer GGP

<figure><img src="../../.gitbook/assets/gogopool_stake_ggp.png" alt=""><figcaption><p>This wallet already has 1.5 GGP staked with a collateralization ratio of 30%, by staking another 4.5 GGP, the future collateralization ratio will be 100%. The user is prompted to approve the transfer of GGP.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/gogopool_deposit_ggp_success.png" alt=""><figcaption><p>Once the GGP transfer is approved by the user, the user can deposit GGP.</p></figcaption></figure>

### Step 4: Stake AVAX

Your wallet provider will prompt you to transfer AVAX

<figure><img src="../../.gitbook/assets/gogopool_deposit_avax.png" alt=""><figcaption><p>Deposit AVAX</p></figcaption></figure>

### Step 5: Minipool created!

Once you deposit AVAX, your Minipool is created! You can use the hash to see the transaction on your block explorer of choice.

<figure><img src="../../.gitbook/assets/gogopool_minipool_successfully_created.png" alt=""><figcaption><p>Minipool successfully created! Use the hash to view the transaction on a block explorer. Proceed to the dashboard to view your Minipool.</p></figcaption></figure>

### Step 6: View the new Minipool on your dashboard

<figure><img src="../../.gitbook/assets/gogopool_minipool_dashboard.png" alt=""><figcaption><p>The dashboard is useful for keeping up to date with your Minipools</p></figcaption></figure>
