---
description: Learn how to register as a hardware provider for a Layer 1 blockchain.
icon: address-card
---

# Hardware Provider Onboarding

This guide is the first step in onboarding as a hardware provider for a Layer 1 blockchain network. It walks you through setting up your environment, generating node keys, securely backing them up, and registering with the Hypha system.

The next guide in this series will walk you through the process of running a Layer 1 node.

{% hint style="info" %}
This guide is specifically for hardware providers and intended for developers familiar with Linux-based systems and command-line operations.
{% endhint %}

## Prerequisites

Before proceeding, ensure the following dependencies are installed on your system:

* [**Go**](https://go.dev/) **1.23 or higher**: Required to build Tartarus.
  * Follow [Go’s official installation instructions](https://go.dev/doc/install) to install the correct version.
  * We do not recommend installing via Ubuntu Apt repositories. These typically provide outdated versions that are not supported.
  * **Important Compatibility Notes:**
    * Go 1.22 and below are untested and may not work as expected.
* **C Compiler (**[**GCC**](https://gcc.gnu.org/) **or** [**Clang**](https://clang.llvm.org/)**)**: Necessary for building dependencies.
* [**jq**](https://github.com/jqlang/jq): A lightweight JSON processor used by the scripts.

### Installing Dependencies on Ubuntu

{% stepper %}
{% step %}
### Install Go

Run the following command to install Go (the command below is for version 1.23.2) on your system, if not already installed:

```bash
sudo rm -rf /usr/local/go # This command removes any existing Go installation. Ensure you have backups if needed.
wget -qO- https://golang.org/dl/go1.23.2.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf - && echo 'export PATH=$PATH:/usr/local/go/bin' 
sudo tee -a $HOME/.bashrc && source $HOME/.bashrc
rm -f go1.23.2.linux-amd64.tar.gz
```

Then, verify the installation:

```
go version
```

For detailed installation instructions, refer to the [official Go documentation](https://go.dev/doc/install).
{% endstep %}

{% step %}
### Install Dependencies

Run the following commands to install the necessary packages:

```bash
sudo apt-get update && sudo apt-get install -y build-essential jq
```
{% endstep %}
{% endstepper %}

***

## Installing Tartarus

[Tartarus](https://github.com/multisig-labs/tartarus/tree/update-db) is a NodeID and key generation tool that simplifies the creation of node keys for Avalanche L1s. Tartarus generates node IDs with customizable prefixes and saves them in a JSON or CSV file compatible with AvalancheGo.

Follow these steps to install it:

{% stepper %}
{% step %}
### Download Tartarus

Clone the Tartarus repository from [Multisig Labs's GitHub Repository](https://github.com/multisig-labs/tartarus) and change the branch to `update-db`

```bash
git clone https://github.com/multisig-labs/tartarus.git
cd tartarus
git checkout update-db
```
{% endstep %}

{% step %}
### Build Tartarus

Navigate to the root directory of the cloned repository (where `main.go` is located) and build the executable.

{% code overflow="wrap" %}
```bash
CGO_CFLAGS="-O -D__BLST_PORTABLE__" CGO_CFLAGS_ALLOW="-O -D__BLST_PORTABLE__" go build -o tartarus main.go
```
{% endcode %}
{% endstep %}
{% endstepper %}

After successful compilation, you should see the `tartarus` executable in your current directory.

***

## Sign Up for a Hypha Account

1. Before uploading node keys, you must first create a Hypha account. Run the signup script provided in the Tartarus repository:

```bash
./scripts/signup.sh
```

2. The script will prompt you for:
   * Your email address
   * A password (make sure to use a unique password not used elsewhere)
   * Password confirmation
3. After signing up, you'll receive a verification email. You must **verify your email address** before proceeding.

## Get Your Hardware Provider ID

Before you can generate and upload keys, you need a Hardware Provider ID. This ID will be assigned to you by the system administrators. Please **contact the administrators** to get your Hardware Provider ID.

## Generating Node Keys

Node keys are cryptographic credentials used to operate L1 nodes. These keys enable secure communication, authentication, and participation in consensus mechanisms. Each node requires a unique set of keys, which are stored in a `nodes.json` file.

Tartarus supports multiple output formats. You can choose between JSON, CSV, or an AvalancheGo-compatible directory.

To generate these keys, follow the steps below:

{% stepper %}
{% step %}
### Generate Node Keys

Run the following command using the Tartarus executable:

<mark style="background-color:yellow;">Be sure to replace</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">`<number_of_nodes>`</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">with how many nodes you want to generate, and</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">`<your_prefix>`</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">with your assigned prefix.</mark>

<pre class="language-bash"><code class="lang-bash"># Basic single-node generation (JSON output)
./tartarus -n <a data-footnote-ref href="#user-content-fn-1">&#x3C;number_of_nodes></a> -o nodes.json

# Generate multiple nodes with prefix (JSON output)
./tartarus -n <a data-footnote-ref href="#user-content-fn-1">&#x3C;number_of_nodes></a> -p <a data-footnote-ref href="#user-content-fn-2">&#x3C;your_prefix></a> -o nodes.json

# Generate keys in AvalancheGo-compatible directory
./tartarus -n <a data-footnote-ref href="#user-content-fn-1">&#x3C;number_of_nodes></a> -o staking-dir

</code></pre>

* Replace `<number_of_nodes>` with the number of nodes allocated to you. (e.g., `10`)
* Replace `<your_prefix>` with your assigned prefix. This prefix ensures uniqueness across the network. (e.g., `GGP`)
* The `-o` flag specifies the output file (`nodes.json`) where the generated keys will be stored.

{% hint style="info" %}
**Available Flags for Generation:**

* `n, --count`: The number of nodes to generate. (Default: `1`)
* `p, --prefix`: The prefix for the node IDs.&#x20;
* `s, --suffix`: The suffix for the node IDs.
* `c, --case-sensitive`: Whether to make the node IDs case-sensitive.
* `o, --output`: The output file or directory for the generated nodes. (Default: `nodes.csv`)
* `v, --verbose`: Whether to print verbose output.
{% endhint %}

> **Note**: The Hypha team will provide your assigned prefix and the number of nodes (allocated number).

> **Note**: Key generation may take some time depending on the number of keys. With prefixes, it typically takes around 1 second per key.
{% endstep %}

{% step %}
### Verify Output

Ensure your output file (CSV or JSON file) or AvalancheGo-compatible directory is created and contains the expected number of keys.

{% hint style="info" %}
## Output Formats

* CSV file (default):
  * Contains node ID, certificate, key, and BLS information
  * Suitable for spreadsheet analysis
* JSON file:
  * Contains the same information in JSON format
  * Required for uploading to the system
* AvalancheGo-compatible directory:
  * Creates a directory with `staker.crt`, `staker.key`, and `signer.key` files
  * Ready to use with AvalancheGo nodes
{% endhint %}
{% endstep %}
{% endstepper %}

{% hint style="danger" %}
Do not use the same keys on both Avalanche Mainnet and Fuji testnet. Always generate new keys for each network to ensure security and isolation.
{% endhint %}

***

## Uploading Node Keys

Once you have generated your node keys, you can upload them to the system:

<mark style="background-color:yellow;">Be sure to replace</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">`YOUR_HARDWARE_PROVIDER_ID`</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">with your hardware provider ID.</mark>

<pre class="language-bash"><code class="lang-bash">./tartarus upload -d nodes.json --hp-id <a data-footnote-ref href="#user-content-fn-3">YOUR_HARDWARE_PROVIDER_ID</a>
</code></pre>

{% hint style="info" %}
#### **Upload Flags**

Required flags for upload:

* `-d, --data-file`: Path to your JSON file containing node data
* `--hp-id`: Your Hardware Provider ID (assigned by administrators)

Optional flags:

* `-e, --email`: Your email address (will prompt if not provided)
* `--password`: Your password (will prompt securely if not provided)
* `--network`: Network for the nodes (default: "fuji")
* `--include-secrets`: Include staker cert, staker key, and BLS private key in the upload
* `--batch-size`: Number of nodes to upload in each batch (default: 25)
{% endhint %}

{% hint style="info" %}
Hypha does not store your private keys. The keys you generate and upload are used solely for network participation and are never retained or stored by us.
{% endhint %}

***

## Security Notes

* Keep your generated keys secure and never share them
* Use a unique password for your account
* The BLS private key is particularly sensitive and should be protected
* Consider using the `--include-secrets` flag only when necessary

***

## Conclusion

By following this guide, node providers can use Tartarus to generate the necessary `NodeID`s and BLS keys, and upload them to the appropriate backend system for their Layer 1 blockchain (such as the Hypha Provider Manager).

Always treat your private keys with extreme care, and ensure they are securely backed up.

If you encounter any issues, refer to the provided scripts or consult the [Tartarus](https://github.com/multisig-labs/tartarus/tree/update-db) documentation. You can also reach out to Hypha support via [Discord](https://discord.gogopool.com/) or the Live Support Chat available on the [Hypha website](https://gogopool.com/).

For instructions on running an L1 node, see the [running-an-l1-node-for-l1marketplace.md](running-an-l1-node-for-l1marketplace.md "mention") guide.

[^1]: Number of nodes allocated to you

[^2]: Your assigned prefix

[^3]: Your Hardware Provider ID that is assigned by administrators
