---
hidden: true
---

# Alignment Plugins for Protocols

Alignment plugins enable protocols to create their own **yield-stripping mechanisms** using stAVAX infrastructure. By creating a custom plugin, protocols can capture and redirect AVAX staking yield for strategic growth, while offering unique incentives to their depositors.

### How Alignment Plugins Work

The mechanism is straightforward:

{% stepper %}
{% step %}
### User Deposit AVAX

User deposits AVAX into your protocol's custom Alignment Plugin contract and receives a custom receipt token (e.g., `xyzAVAX`).
{% endstep %}

{% step %}
### Yield Generation

The plugin automatically routes the deposited AVAX to the `stAVAX` vault, where it begins generating yield.
{% endstep %}

{% step %}
### Yield Harvest

The protocol programmatically harvests the generated yield while ensuring the user's original principal deposit remains untouched.
{% endstep %}

{% step %}
### Yield Redirection

The protocol then programmatically directs this harvested yield to its chosen onchain destination, such as a treasury, a liquidity pool, or a rewards contract.
{% endstep %}

{% step %}
### User Incentives

In exchange for providing the yield, users receive the protocol's unique rewards (e.g., its native token, airdrop points, or other perks).
{% endstep %}

{% step %}
### Withdrawal

Users can withdraw their original AVAX principal, subject to any custom rules (like lockups) the protocol defines in its plugin.
{% endstep %}
{% endstepper %}

Each plugin can issue its own custom receipt token (e.g., `xyzAVAX`) and operates independently with its own set of rules.

### Key Benefits for Protocols

* **Sustainable Funding**: Access a continuous and external source of revenue from `stAVAX` yield without needing to sell your native token or rely on inflationary emissions.
* **Immediate Access to Capital & Liquidity**: Launch with committed capital by accepting user deposits into pre-launch vaults before a mainnet is live.
* **Accelerated Growth**: Use the captured yield to directly fund strategic actions that can rapidly bootstrap your protocol's most important metrics.
* **Sustainable Incentives**: Fund user rewards and liquidity programs with external yield earned from staked AVAX, providing a sustainable alternative to inflationary token emissions.
* **User Alignment**: Aligns depositors by offering them exposure to a protocol's success through rewards, while they retain their underlying AVAX principal.

### Common Use Cases for Protocols

Alignment Plugins are flexible tools that can be adapted to achieve a variety of goals. Here are some common strategies:

* **Bootstrap Liquidity**: Redirect yield to DEX incentives to create sustainable liquidity for a protocol's token without diluting it through emissions.
* **Raise Capital**: Create a pre-deposit vault where users lock AVAX for a set period. Your protocol retains the generated yield to fund operations, and in return, users receive their principal back plus an allocation of your project's tokens.
* **Monetize Bridge Flows**: Monetize your bridge by routing bridged AVAX through a plugin, capturing the yield as protocol revenue while sending AVAX to the user on your chain.
* **Incentivize Validators**: Stream the captured yield directly to your validator set, making it more profitable and attractive to run a node and rapidly decentralizing your network.

### Customization Options for Plugins

Protocols have full control over the key parameters of their plugin:

* **Yield Distribution**: You can specify the exact percentage of yield to be captured (from 0% to 100%) and programmatically define its onchain destination.
* **Lockup Periods**: Optional **time-based** or **conditional locks** on user deposits.
* **Reward Structure**: The design of the incentive system, using native tokens, points, revenue sharing, or other perks.
* **Harvest Schedule**: The frequency at which generated yield is collected and distributed.

### Getting Started for Plugins

While the plugin contracts are open-source, launching an official Alignment Plugin is a collaborative process. We work with teams to ensure security, best practices, and successful integration into the broader Hypha ecosystem.

{% stepper %}
{% step %}
### Review the Template

Examine the `pstAVAX` contract to understand the base yield-stripping mechanism. The generic, forkable version of this is called the `lstAVAX` open-source template.
{% endstep %}

{% step %}
### Define a Strategy

Determine how the captured yield will be used and how depositors will be incentivized to participate.
{% endstep %}

{% step %}
### Fork and Customize

Fork the `lstAVAX` template and modify the smart contract to implement the desired logic.
{% endstep %}

{% step %}
### Deploy and Integrate

Deploy the custom plugin and integrate it with the protocol's existing infrastructure. Then, begin accepting user deposits to power your protocol's growth.
{% endstep %}
{% endstepper %}

For technical support and integration assistance, please contact the team.

