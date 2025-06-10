---
description: Learn how to run an L1 node.
icon: laptop-code
---

# Running an L1 Node for Hypha

This guide is part of a series covering the end-to-end process for participating in a Layer 1 blockchain as a hardware provider. It focuses on setting up and running a node using AvalancheGo on any Avalanche-based L1.

This guide is intended for developers familiar with Linux-based systems and command-line operations.

{% hint style="info" %}
This guide is specifically for hardware providers. If you’re looking to become a validator by staking, refer to the dedicated validator staking guide.
{% endhint %}

***

## Hardware Requirements

Below are the minimum hardware specifications for running an L1 node on Fuji testnet and Mainnet.

| **Component**        | **Fuji Testnet** | **Mainnet**      |
| -------------------- | ---------------- | ---------------- |
| **CPU vCores**       | 4 (2 dedicated)  | 4 (2 dedicated)  |
| **RAM**              | 4GB              | 8GB              |
| **Storage**          | 200GB SSD        | 300GB SSD        |
| **Network In/Out**   | 100Mb/100Mb      | 5Gb/5Gb          |
| **Operating System** | Ubuntu 22.04 LTS | Ubuntu 24.04 LTS |

{% hint style="success" %}
While ARM64 binaries are available, we recommend using x86 (AMD64) for stability and performance with most Avalanche-based L1 nodes at this time.
{% endhint %}

{% hint style="warning" %}
These are baseline numbers for getting started today and are subject to change since storage, CPU, and memory requirements will increase as the blockchain grows. Nearly half of the recommended storage is allocated for the P-Chain.

Using a system that can be easily expanded is highly recommended.&#x20;
{% endhint %}

***

## Suggested Hosting Providers

* [Contabo](https://contabo.com/)
* [Amazon Web Services (AWS)](https://aws.amazon.com/)
* [OVH](https://www.ovhcloud.com/en/)
* [Netcup](https://www.netcup.com/en)
* Other cloud providers or dedicated server providers meeting the hardware requirements.

***

## Installing AvalancheGo

The first step is installing AvalancheGo, the client software for running L1 nodes. You can install it either [manually](https://docs.avax.network/nodes/run-a-node/manually#run-with-a-pre-built-binary) or [via the install script](https://docs.avax.network/nodes/using-install-script/installing-avalanche-go).

{% hint style="success" %}
Before installing AvalancheGo via your preferred method, we recommend you read on below for your respective install method.
{% endhint %}

Once AvalancheGo is installed, proceed to configure your node using one of the methods below.

***

## Manual Installation Steps

{% hint style="warning" %}
#### Finding L1 Specific Information

You can find L1 specific information like `subnet_ID` and `VM_ID` by finding the L1 [here](https://subnets.avax.network/).
{% endhint %}

If you installed AvalancheGo manually, follow these steps to configure your node:

{% stepper %}
{% step %}
### Download and Install the Subnet EVM Binary

Before we can start our node, we need to add the Subnet EVM binary to the machine.&#x20;

Run the following commands to download and place the Subnet EVM binary in the correct directory.

<mark style="background-color:yellow;">Be sure to replace</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">`<VM_ID>`</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">with the actual VM ID for your Subnet before running the command.</mark>

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash"># Fetch the latest release download URL and download the tarball
curl -s https://api.github.com/repos/ava-labs/subnet-evm/releases/latest | jq -r '.assets[] | select(.name | test("^subnet-evm_[0-9.]+_linux_amd64\\.tar\\.gz$")) | .browser_download_url' | xargs curl -L -O

# Create the plugins directory if it doesn't exist
mkdir -p "$HOME/.avalanchego/plugins"

# Extract the subnet-evm binary from the tarball
tar -xzf subnet-evm_*_linux_amd64.tar.gz subnet-evm

# Move the extracted binary to the plugins directory with a new name
// highlight-next-line
mv subnet-evm "$HOME/.avalanchego/plugins/<a data-footnote-ref href="#user-content-fn-1">&#x3C;VM ID></a>"

# Optionally, clean up the downloaded tarball
rm subnet-evm_*_linux_amd64.tar.gz
</code></pre>

{% hint style="warning" %}
#### Configuration Details: VM ID

The `VM ID` is a cryptographic hash that uniquely identifies the Subnet EVM binary. AvalancheGo uses this ID to locate and execute the correct virtual machine for your Subnet.

**How to Find the Correct VM ID?**

You can find the correct VM ID (e.g., `knwdavfavsrcds7PKZmVBd51ZGxkhRQsC9xUHzSNHdegDCWBL`) on the L1's [Avalanche Subnet Explorer](https://subnets.avax.network/subnets/) under the _Chain Info_ section, or in the official documentation provided by your L1 project.\


Using the wrong VM ID will prevent connection to your intended blockchain.
{% endhint %}
{% endstep %}

{% step %}
### Configure AvalancheGo Startup

Before starting the node, add the `-partial-sync-primary-network` flag and the `-track-subnets` flag with your target L1's Subnet ID to the startup command.&#x20;

Your startup command should look like this:

<mark style="background-color:yellow;">Make sure to replace</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">`<VERSION>`</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">and</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">`<Subnet_ID>`</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">with the correct AvalancheGo version and your specific Subnet ID before running the command.</mark>

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash">./avalanchego-<a data-footnote-ref href="#user-content-fn-2">&#x3C;VERSION></a>-linux/avalanchego --partial-sync-primary-network --track-subnets=<a data-footnote-ref href="#user-content-fn-3">&#x3C;Subnet_ID></a>
</code></pre>

For more details on available configurations, see the [AvalancheGo Configs and Flags documentation](https://docs.avax.network/nodes/configure/configs-flags).

{% hint style="info" %}
#### Configuration Details: Subnet ID & Network

**`<Subnet_ID>`**: This is the unique identifier for the L1 blockchain (Subnet) you want your node to track and validate.

**Examples:**

* **Coqnet:** `5moznRzaAEhzWkNTQVdT1U4Kb9EU7dbsKZQNmHwtN5MGVQRyT`
* **COQnet Fuji Testnet:** `4YurNFwLzhGUrYyihDnUUc2L199YBnFeWP3fhJKmDDjkbvy8G`
{% endhint %}
{% endstep %}

{% step %}
### Run at Startup

Configure this command to run automatically at startup using your preferred method (e.g., `systemd`, `supervisor`). This ensures your node restarts if the server reboots.

And that's it! :tada: Your node should now be running and tracking the specified L1 Subnet. You now have a working L1 node running on Avalanche Mainnet.

{% hint style="warning" %}
Remember that it can take a significant amount of time for your node to fully sync with the Primary Network and the tracked Subnet.
{% endhint %}
{% endstep %}
{% endstepper %}

***

{% hint style="warning" %}
#### Finding L1 Specific Information

You can find L1 specific information like `subnet_ID` and `VM_ID` by finding the L1 [here](https://subnets.avax.network/).
{% endhint %}

## Script Installation Steps

If you used the AvalancheGo install script, follow these steps to configure your node:

{% stepper %}
{% step %}
### Stop the AvalancheGo Process

Stop the `avalanchego` service before making changes:

```bash
sudo systemctl stop avalanchego
```
{% endstep %}

{% step %}
### Download and Install the Subnet EVM Binary

Run the following commands to download and place the Subnet EVM binary in the correct directory:

<mark style="background-color:yellow;">Be sure to replace</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">`<VM_ID>`</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">with the actual VM ID for your Subnet before running the command.</mark>

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash"># Fetch the latest release download URL and download the tarball
curl -s https://api.github.com/repos/ava-labs/subnet-evm/releases/latest | jq -r '.assets[] | select(.name | test("^subnet-evm_[0-9.]+_linux_amd64\\.tar\\.gz$")) | .browser_download_url' | xargs curl -L -O

# Create the plugins directory if it doesn't exist
mkdir -p "$HOME/.avalanchego/plugins"

# Extract the subnet-evm binary from the tarball
tar -xzf subnet-evm_*_linux_amd64.tar.gz subnet-evm

# Move the extracted binary to the plugins directory with a new name
mv subnet-evm "$HOME/.avalanchego/plugins/<a data-footnote-ref href="#user-content-fn-1">&#x3C;VM ID></a>"

# Optionally, clean up the downloaded tarball
rm subnet-evm_*_linux_amd64.tar.gz
</code></pre>

{% hint style="warning" %}
#### Configuration Details: VM ID

The `VM ID` is a cryptographic hash that uniquely identifies the Subnet EVM binary. AvalancheGo uses this ID to locate and execute the correct virtual machine for your Subnet.

**How to Find the Correct VM ID?**

You can find the correct VM ID (e.g., `knwdavfavsrcds7PKZmVBd51ZGxkhRQsC9xUHzSNHdegDCWBL`) on the L1's [Avalanche Subnet Explorer](https://subnets.avax.network/subnets/) under the _Chain Info_ section, or in the official documentation provided by your L1 project.\


Using the wrong VM ID will prevent connection to your intended blockchain.
{% endhint %}
{% endstep %}

{% step %}
### Configure Tracked Subnets

Add the Subnet ID of the L1 to the AvalancheGo configuration file. This file is typically located at `$HOME/.avalanchego/configs/node.json`.

<mark style="background-color:yellow;">Be sure to replace</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">`<Subnet_ID>`</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">with the actual Subnet ID you intend to track before running the command.</mark>

<pre class="language-json"><code class="lang-json">{
    "track-subnets": "<a data-footnote-ref href="#user-content-fn-4">&#x3C;Subnet_ID></a>",
    // ... other existing configurations ...
}
</code></pre>

{% hint style="info" %}
#### Configuration Details: Subnet ID & Network

**`Subnet_ID`**: This is the unique identifier for the L1 blockchain (Subnet) you want your node to track and validate.

**Examples:**

* **Coqnet:** `5moznRzaAEhzWkNTQVdT1U4Kb9EU7dbsKZQNmHwtN5MGVQRyT`
* **COQnet Fuji Testnet:** `4YurNFwLzhGUrYyihDnUUc2L199YBnFeWP3fhJKmDDjkbvy8G`
{% endhint %}
{% endstep %}

{% step %}
### Enable Partial Sync in the Unit File

It's highly recommended to enable the `-partial-sync-primary-network` flag. This prevents your node from downloading the full history of the Avalanche C-Chain, saving considerable storage space.

Edit the unit file located at `/etc/systemd/system/avalanchego.service` to include the `--partial-sync-primary-network` flag.

Simply add the `--partial-sync-primary-network` flag to the `ExecStart` command in the `[Service]` section.&#x20;

{% code overflow="wrap" %}
```diff
-ExecStart=/path/to/avalanchego --config-file=/path/to/.avalanchego/configs/node.json
+ExecStart=/path/to/avalanchego --config-file=/path/to/.avalanchego/configs/node.json --partial-sync-primary-network
```
{% endcode %}

The updated file should look like this:

{% code overflow="wrap" %}
```toml
[Unit]
Description=AvalancheGo systemd service
StartLimitIntervalSec=0

[Service]
Type=simple
User=ubuntu # Replace with the user running avalanchego
WorkingDirectory=/home/ubuntu # Replace with the user's home or avalanchego directory
ExecStart=/home/ubuntu/avalanche-node/avalanchego --config-file=/home/ubuntu/.avalanchego/configs/node.json --partial-sync-primary-network
LimitNOFILE=32768
Restart=always
RestartSec=1

[Install]
WantedBy=multi-user.target
```
{% endcode %}

<mark style="background-color:yellow;">Be sure to replace</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">`ubuntu`</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">in</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">`User`</mark><mark style="background-color:yellow;">,</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">`WorkingDirectory`</mark><mark style="background-color:yellow;">, and</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">`ExecStart`</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">with the correct username and paths for your system.</mark>
{% endstep %}

{% step %}
### Reload and Restart the Service

Reload the `systemd` configuration and restart the `avalanchego` service:

```bash
sudo systemctl daemon-reload
sudo systemctl start avalanchego
```

And that's it! :tada: Your node should now be running and tracking the specified L1 Subnet. You now have a working L1 node running on Avalanche Mainnet.
{% endstep %}
{% endstepper %}

***

## Monitoring Your Node

Once your node is running, you can monitor its status and check logs with the following commands:

```bash
sudo systemctl status avalanchego
journalctl -u avalanchego -f
```

## Checking Sync Progress

To check if your node has finished bootstrapping (syncing) with the Avalanche Primary Network (P-Chain), you can execute the following command.

{% code overflow="wrap" %}
```bash
curl -X POST -H 'content-type: application/json' -d '{"jsonrpc":"2.0","id":1,"method":"info.isBootstrapped","params":{"chain":"P"}}' 127.0.0.1:9650/ext/info
```
{% endcode %}

To check the bootstrapping status of **your specific L1 Subnet**, replace the `chain` parameter with your L1's Chain ID (not the Subnet ID).

{% hint style="warning" %}
#### Configuration Details: Chain Alias/ID for Bootstrapping Check

* **Primary Network P-Chain (General):** Use `"P"` or the P-Chain's actual ID (e.g., `11111111111111111111111111111111LpoYY` for Mainnet and Fuji).
* **L1 Subnet's Chain:** You'll need the `chainID`(or Blockchain ID) of your L1. This is different from the Subnet ID.

**Example:**

* `{"chain":"23aQU1537YseCJmXW11XHjPra6bptBSps5D4xXupt8hN2QUeaG"}`
* `{"chain":"[Your_L1_Chain_ID]"}`
{% endhint %}

A response of  `"isBootstrapped":true}` indicates the chain is bootstrapped.

## Conclusion

If you encounter any issues, refer to the [AvalancheGo documentation](https://docs.avax.network/) or reach out to Hypha support for assistance on [Discord](https://discord.gogopool.com/) or via Live Support Chat on the [Hypha website](https://gogopool.com/).

[^1]: Replace with the correct VM ID

[^2]: Replace with your AvalancheGo version

[^3]: Replace with your specific Subnet ID

[^4]: Replace with the actual Subnet ID
