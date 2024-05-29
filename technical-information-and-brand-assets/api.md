---
description: >-
  Details and documentation for accessing and using the GoGoPool API for
  developers.
---

# 💻 API

The GoGoPool API is a decentralized liquid staking protocol built on Avalanche that provides a robust and scalable solution for blockchain data. The API offers a wide range of endpoints that enable users to access various data points, including token prices, staking information, and validator data.

## Available Data

The GoGoPool API provides access to the following data points:

* **Token prices**: Get current and historical token prices, including `GGP`, `AVAX`, and USD prices.
* **Staking information**: Retrieve staking-related data, such as staker information, minipool data, and validator information.
* **Validator data**: Access data on active validators, including their node IDs, staking information, and rewards.
* **Rewards**: Calculate rewards based on `ggpStaked` and `avaxStaked` amounts or retrieve rewards data for a specific address.
* **Metrics**: Retrieve various metrics, such as ggAVAX APY, total assets, and staking information.
* **Feature flags**: Get feature flags for the current environment.

### Code Examples

{% tabs %}
{% tab title="cURL" %}
Here's an example of retrieving the current GGP price in AVAX using cURL:

<pre class="language-json"><code class="lang-json"><strong>curl -X GET \\
</strong>  'https://api.gogopool.com/prices' \
  -H 'accept: application/json'
</code></pre>

This will return a JSON response with the current `GGP` price in `AVAX`.
{% endtab %}

{% tab title="Python" %}
Here's an example of retrieving the current token prices using Python:

```python
import requests

response = requests.get('https://api.gogopool.com/prices')

if response.status_code == 200:
    data = response.json()
    print(data)
else:
    print('Error:', response.status_code)
```

This will print the current token prices in JSON format.
{% endtab %}
{% endtabs %}

### API Endpoints

Here are some examples of API endpoints:

* `GET /prices/tj`: Get the current token prices on Trader Joe.
* `GET /ggAvax`: Get the various amounts in the ggAVAX Liquid Staking pool.
* `GET /validators`: Get all currently active validators from Glacier API.
* `GET /rewards/byStake`: Calculate the rewards given `ggpStaked` and `avaxStaked` amounts.
* `GET /metrics`: Get the current metrics, such as ggAVAX APY and total assets.

For a comprehensive list of API endpoints and parameters, please refer to the [GoGoPool OpenAPI page](https://api.gogopool.com).
