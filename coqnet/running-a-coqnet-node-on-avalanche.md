---
icon: laptop-code
description: Learn how to run a Coqnet Node.
---

# Running a Coqnet Node on Avalanche

This guide is part of a series covering the end-to-end process of participating in Coqnet as a hardware provider. It focuses on setting up and running a Coqnet node on the Avalanche Mainnet.

This guide is intended for developers familiar with Linux-based systems and command-line operations.

{% hint style="info" %}
This guide is specifically for hardware providers. If you’re looking to become a validator by staking COQ, refer to the [coqnet-climax-how-to-stake-coq-and-become-a-validator.md](coqnet-climax-how-to-stake-coq-and-become-a-validator.md "mention")
{% endhint %}

***

## Hardware Requirements

Below are the minimum hardware specifications for running a Coqnet node on Fuji testnet and Mainnet.

| **Component**        | **Fuji Testnet** | **Mainnet**      |
| -------------------- | ---------------- | ---------------- |
| **CPU vCores**       | 4 (2 dedicated)  | 4 (2 dedicated)  |
| **RAM**              | 4GB              | 8GB              |
| **Storage**          | 200GB SSD        | 1000GB NVMe SSD  |
| **Network In/Out**   | 100Mb/100Mb      | 5Gb/5Gb          |
| **Operating System** | Ubuntu 22.04 LTS | Ubuntu 24.04 LTS |

{% hint style="success" %}
While ARM64 binaries are available, we recommend using x86 (AMD64) for Coqnet nodes at this time.
{% endhint %}

{% hint style="warning" %}
Over time, storage, CPU, and memory requirements will increase as the blockchain grows. These are baseline numbers for getting started today and are subject to change. Using a system that can be easily expanded is highly recommended. Nearly half of the recommended storage is allocated for the P-Chain.
{% endhint %}

***

## Suggested Hosting Providers

* [Akamai Connected Cloud](https://www.linode.com/) (formerly Linode)
* [Contabo](https://contabo.com/)
* AWS

***

## Installing AvalancheGo

The first step is installing AvalancheGo, the client software for running Coqnet nodes. You can install it either [manually](https://docs.avax.network/nodes/run-a-node/manually#run-with-a-pre-built-binary) or [via the install script](https://docs.avax.network/nodes/using-install-script/installing-avalanche-go).

{% hint style="success" %}
Before installing AvalancheGo via your preferred method, we recommend you read on below for your respective install method.
{% endhint %}

Once AvalancheGo is installed, proceed to configure your node using one of the methods below.

***

## Manual Installation Steps

If you installed AvalancheGo manually, follow these steps to configure your node:

{% stepper %}
{% step %}
### Download and Install the Subnet EVM Binary

Run the following commands to download and place the Subnet EVM binary in the correct directory:

```bash
# Fetch the latest release download URL and download the tarball
curl -s https://api.github.com/repos/ava-labs/subnet-evm/releases/latest | jq -r '.assets[] | select(.name | test("^subnet-evm_[0-9.]+_linux_amd64\\.tar\\.gz$")) | .browser_download_url' | xargs curl -L -O

# Create the plugins directory if it doesn't exist
mkdir -p "$HOME/.avalanchego/plugins"

# Extract the subnet-evm binary from the tarball
tar -xzf subnet-evm_*_linux_amd64.tar.gz subnet-evm

# Move the extracted binary to the plugins directory with a new name
mv subnet-evm "$HOME/.avalanchego/plugins/knwdavfavsrcds7PKZmVBd5iZGXkhRQsC9xUHzSNHdegDCWBL"

# Optionally, clean up the downloaded tarball
rm subnet-evm_*_linux_amd64.tar.gz
```
{% endstep %}

{% step %}
### Start the Node with Required Flags

Add the flags `--partial-sync-primary-network` and `--track-subnets` with Coqnet’s Subnet ID to the startup command. Your command should look like this:

```bash
./avalanchego-<VERSION>-linux/avalanchego --partial-sync-primary-network --track-subnets=5moznRzaAEhzWkNTQVdT1U4Kb9EU7dbsKZQNmHwtN5MGVQRyT
```

> For Fuji Testnet, use the Subnet ID `4YurNFwLzhGUrYyihDnUUc2L199YBnFeWP3fhJKmDDjkbvy8G`

For more details on available configurations, see the [AvalancheGo Configs and Flags documentation](https://docs.avax.network/nodes/configure/configs-flags).
{% endstep %}

{% step %}
### Set Up Automatic Startup

Configure your preferred method to ensure the node starts automatically by running the startup command on system boot. For example, you can use `systemd` to create a service unit file.

And that's it! :tada: You now have a working Coqnet node running on Avalanche Mainnet.
{% endstep %}
{% endstepper %}

***

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

```bash
# Fetch the latest release download URL and download the tarball
curl -s https://api.github.com/repos/ava-labs/subnet-evm/releases/latest | jq -r '.assets[] | select(.name | test("^subnet-evm_[0-9.]+_linux_amd64\\.tar\\.gz$")) | .browser_download_url' | xargs curl -L -O

# Create the plugins directory if it doesn't exist
mkdir -p "$HOME/.avalanchego/plugins"

# Extract the subnet-evm binary from the tarball
tar -xzf subnet-evm_*_linux_amd64.tar.gz subnet-evm

# Move the extracted binary to the plugins directory with a new name
mv subnet-evm "$HOME/.avalanchego/plugins/knwdavfavsrcds7PKZmVBd5iZGXkhRQsC9xUHzSNHdegDCWBL"

# Optionally, clean up the downloaded tarball
rm subnet-evm_*_linux_amd64.tar.gz
```
{% endstep %}

{% step %}
### Update the Configuration File

Add the following attribute to the configuration file located at `$HOME/.avalanchego/configs/node.json`:

```json
{
    "track-subnets": "5moznRzaAEhzWkNTQVdT1U4Kb9EU7dbsKZQNmHwtN5MGVQRyT",
    ... // rest of config file
}
```

> For Fuji Testnet, use the Subnet ID `4YurNFwLzhGUrYyihDnUUc2L199YBnFeWP3fhJKmDDjkbvy8G`
{% endstep %}

{% step %}
### Enable Partial Sync in the Unit File

Edit the unit file located at `/etc/systemd/system/avalanchego.service` to include the `--partial-sync-primary-network` flag.

Simply add the `--partial-sync-primary-network` flag to the `ExecStart` command in the `[Service]` section. The updated file should look like this:

```toml
[Unit]
Description=AvalancheGo systemd service
StartLimitIntervalSec=0

[Service]
Type=simple
User=ubuntu
WorkingDirectory=/home/ubuntu
ExecStart=/home/ubuntu/avalanche-node/avalanchego --config-file=/home/ubuntu/.avalanchego/configs/node.json --partial-sync-primary-network
LimitNOFILE=32768
Restart=always
RestartSec=1

[Install]
WantedBy=multi-user.target
```

{% hint style="info" %}
**Why Updating the Unit File instead of the Configuration File?**

Adding this flag to the unit file ensures it remains active even if the config file is reset or changed, preventing your storage from being overwhelmed by C-Chain data during restarts.
{% endhint %}
{% endstep %}

{% step %}
### Reload and Restart the Service

Reload the systemd configuration and restart the `avalanchego` service:

```bash
sudo systemctl daemon-reload
sudo systemctl start avalanchego
```

And that's it! You now have a working Coqnet node running on the Avalanche Mainnet.
{% endstep %}
{% endstepper %}

***

## Monitoring Your Node

Once your node is running, you can monitor its status using standard `systemctl` commands:

```bash
sudo systemctl status avalanchego
journalctl -u avalanchego -f
```

## Checking Sync Progress

To check the progress of syncing on the Avalanche Mainnet, you can execute the following command.

```bash
curl -X POST -H 'content-type: application/json' -d '{"jsonrpc":"2.0","id":1,"method":"info.isBootstrapped","params":{"chain":"EyWDF1cGmMKXRi4d5Mb1kVNnB1zHWvMPGQM5uHgizNGFTvsTn"}}' 127.0.0.1:9650/ext/info
```

## Conclusion

If you encounter any issues, refer to the [AvalancheGo documentation](https://docs.avax.network/) or reach out to GoGoPool support for assistance on [Discord](https://discord.gogopool.com/) or via Live Support Chat on the [GoGoPool website](https://www.gogopool.com/).
