---
description: Register as a hardware provider for Coqnet.
icon: address-card
---

# Hardware Provider Onboarding

This guide is part of a series covering the end-to-end process of participating in Coqnet as a hardware provider. It walks you through setting up your environment, generating node keys, securely backing them up, and uploading them to the GoGoPool Provider Manager.

This guide is intended for developers familiar with Linux-based systems and command-line operations.

{% hint style="info" %}
This guide is specifically for hardware providers. If you’re looking to become a validator by staking COQ, refer to the [coqnet-climax-how-to-stake-coq-and-become-a-validator.md](coqnet-climax-how-to-stake-coq-and-become-a-validator.md "mention")
{% endhint %}

## Prerequisites

Before proceeding, ensure the following dependencies are installed on your system:

* [**Go**](https://go.dev/) **1.22 or higher**: Required to build Tartarus.
* **C Compiler (**[**GCC**](https://gcc.gnu.org/) **or** [**Clang**](https://clang.llvm.org/)**)**: Necessary for building dependencies.
* [**jq**](https://github.com/jqlang/jq): A lightweight JSON processor used by the scripts.

### Installing Dependencies on Ubuntu

Run the following command to install Go 1.23 on your system, if not already installed:

```bash
sudo rm -rf /usr/local/go # This command removes any existing Go installation. Ensure you have backups if needed.
wget -qO- https://golang.org/dl/go1.23.2.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf - && echo 'export PATH=$PATH:/usr/local/go/bin' 
sudo tee -a $HOME/.bashrc && source $HOME/.bashrc
rm -f go1.22.0.linux-amd64.tar.gz
```

For detailed installation instructions, refer to the [official Go documentation](https://go.dev/doc/install).

Run the following commands to install the necessary packages:

```bash
sudo apt-get update && sudo apt-get install -y build-essential jq
```

***

## Installing Tartarus

[Tartarus](https://github.com/multisig-labs/tartarus) is a NodeID and key generation tool that simplifies the creation of node keys for Coqnet. Tartarus generates node IDs with customizable prefixes and saves them in a JSON file compatible with AvalancheGo.

Follow these steps to install it:

{% stepper %}
{% step %}
### Download Tartarus

Clone the Tartarus repository from [Multisig Labs's GitHub Repository](https://github.com/multisig-labs/tartarus):

```bash
git clone https://github.com/multisig-labs/tartarus.git
```
{% endstep %}

{% step %}
### Build Tartarus

Navigate to the directory containing `main.go` and build the executable:

```bash
cd tartarus
go build -o tartarus main.go
```
{% endstep %}
{% endstepper %}

After successful compilation, you should see the `tartarus` executable in your current directory.

***

## Generating Node Keys

Node keys are cryptographic credentials used to operate Coqnet nodes. These keys enable secure communication, authentication, and participation in consensus mechanisms. Each node requires a unique set of keys, which are stored in a `nodes.json` file.

The `nodes.json` file contains the following values for each node:

* `node_id` : Unique identifier for the node.
* `cert` : TLS certificate for secure communication.
* `key` : Private key corresponding to the TLS certificate, used for authentication.
* `bls_private` : Private key for Boneh-Lynn-Shacham (BLS) signatures.
* `bls_public` : Public key corresponding to the `bls_private` key.
* `bls_signature` : BLS cryptographic signature used for validation purposes.

To generate these keys, follow the steps below:

{% stepper %}
{% step %}
### Generate Keys

Run the following command using the Tartarus executable:

```bash
./tartarus -n <number_of_nodes> -p <your_prefix> -o nodes.json
```

* Replace `<number_of_nodes>` with the number of nodes allocated to you. For example, if you are allocated to run 5 nodes, replace `<number_of_nodes>` with `5`.
* Replace `<your_prefix>` with your assigned prefix. This prefix ensures uniqueness across the network.
* The `-o` flag specifies the output file (`nodes.json`) where the generated keys will be stored.

```bash
./tartarus -n 5 -p GGP -o nodes.json
```

> **Note**: The GoGoPool team will provide your assigned prefix and the number of nodes (allocated number).

> **Note**: Key generation may take some time depending on the number of keys. With prefixes, it typically takes around 1 second per key.
{% endstep %}

{% step %}
### Verify Output

Ensure the `nodes.json` file is created and contains the expected number of keys.

The file structure should resemble the following:

```json
{
  "nodes": [
    {
      "node_id": "your_node_id",
      "cert": "your_node_cert",
      "key": "your_node_key",
      "bls_private": "your_node_bls_private",
      "bls_public": "your_node_bls_public",
      "bls_signature": "your_node_bls_signature"
    }
  ]
}
```
{% endstep %}
{% endstepper %}

{% hint style="danger" %}
Do not use the same keys on both Avalanche mainnet and Fuji testnet. Always generate new keys for each network to ensure security and isolation.
{% endhint %}

***

## Backing Up Keys Securely

Securing your node keys is **critical** to maintaining the integrity of your participation in Coqnet. Here are some best practices to follow:

1. **Store Keys Offline**\
   Copy the generated `nodes.json` file to a secure, offline location.
2. **Secure the Backup**\
   Use encryption tools like `gpg` or BitLocker to protect the backup.
3. **Limit Access**\
   Ensure only authorized personnel have access to the backup.

***

## Signing Up for an Account with GoGoPool

To upload your keys and participate in Coqnet, you’ll need to create an account with GoGoPool.

{% stepper %}
{% step %}
### Execute the Signup Script

Run the `signup.sh` script to create an account:

```bash
./coq_scripts/signup.sh
```
{% endstep %}

{% step %}
### Enter Credentials

* Provide your email address.
* Create a strong, unique password.
* Confirm the password.
{% endstep %}

{% step %}
### Verify Account

After successful signup, check your email for a verification link and verify your account. The email should be from [notifications@gogopool.com](mailto:notifications@gogopool.com). If you don’t receive the verification email, do not forget to check your spam folder.
{% endstep %}

{% step %}
### Contact the GoGoPool Representative

Once verified, message [@chand1012](https://t.me/chand1012), our GoGoPool representative, on Telegram with your email and organization name. He will add your organization to the database, enabling you to upload your keys.
{% endstep %}
{% endstepper %}

***

## Uploading Keys to GoGoPool Provider Manager

After signing up, you’ll need to upload your keys to the **GoGoPool Provider Manager**.

{% hint style="info" %}
GoGoPool does not store your private keys. The keys you generate and upload are used solely for network participation and are never retained or stored by us.
{% endhint %}

{% stepper %}
{% step %}
### Authenticate and Upload

Use the `post_nodes.sh` script to upload your keys:

```bash
./coq_scripts/post_nodes.sh -d nodes.json -C 48765 # Fuji Coqnet's EVM Chain ID
```

{% hint style="info" %}
The following steps are for uploading keys to the Fuji Testnet. The process is similar for Avalanche Mainnet, with the only difference being the EVM Chain ID.
{% endhint %}
{% endstep %}

{% step %}
### Enter Credentials

Provide the email and password used during signup.
{% endstep %}

{% step %}
### Monitor Upload

The script will transform and upload the keys. Ensure the process completes without errors.
{% endstep %}
{% endstepper %}

***

## Transform Keys for AvalancheGo

The keys generated by Tartarus need to be transformed into a format compatible with [AvalancheGo](https://github.com/ava-labs/avalanchego), the client software for running Coqnet nodes.

{% stepper %}
{% step %}
### Run the Conversion Command

Execute the following command to transform the keys:

```bash
go run cmd/convert/main.go -i nodes.json -o keys
```

This will create a directory called `keys`, containing all the keys in the proper format for copying to your nodes.
{% endstep %}

{% step %}
### Verify Output

Ensure the `keys` directory is created and contains the expected number of keys. The directory structure should resemble the following:

```bash
tartarus/keys
├── NodeID-YOUR_NODE_ID
│   ├── signer.key # BLS private key for signing consensus messages
│   ├── staker.crt # TLS certificate for secure communication
│   └── staker.key # Private key corresponding to the TLS certificate
```
{% endstep %}
{% endstepper %}

***

## Conclusion

By following this guide, you’ve successfully generated, backed up, and uploaded your node keys to the GoGoPool Provider Manager.

If you encounter any issues, refer to the provided scripts or reach out to GoGoPool support for assistance on [Discord](https://discord.gogopool.com/) or Live Support Chat on the [GoGoPool website](https://www.gogopool.com/).

For instructions on running a Coqnet node, see the [running-a-coqnet-node-on-fuji-testnet.md](running-a-coqnet-node-on-fuji-testnet.md "mention") guide.
