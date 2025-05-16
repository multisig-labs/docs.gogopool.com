---
description: What are they, and why does my Minipool need them?
---

# 🔑 Avalanche BLS Keys

## What are BLS Keys?

BLS, or [Boneh-Lynn-Shacham](https://en.wikipedia.org/wiki/BLS\_digital\_signature), is a digital signature scheme that uses keys for secure signing and verification. Unlike traditional signatures, BLS allows combining numerous signatures into a single, compact one, enabling efficient verification of multiple signers simultaneously. This efficient and secure approach makes BLS keys valuable in blockchain systems, decentralized identity solutions, and multi-party computations, where managing numerous signatures or verifications is crucial.

## Why is Avalanche requiring my Node to have them?

[Avalanche](https://www.avax.network/) is rolling out a new feature called [Avalanche Warp Messaging (AWM)](https://docs.avax.network/build/cross-chain/awm/overview). This new feature allows cross-chain communication without any additional trust assumptions apart from the existing validator set, making cross-chain transfers more secure. In order to verify these messages, Avalanche is requiring validator nodes to [hold BLS Keys](https://github.com/ava-labs/avalanchego/blob/6dcd8e8adaeacb6d9e7f46654bfbd93639cbd22a/vms/platformvm/warp/README.md#bls-multi-signatures-with-public-key-aggregation) in order to sign Warp messages.

## How do I acquire my Node’s BLS Public Keys?

Node providers will be required to provide their BLS public keys in order to continue staking.

### One-Click Minipools

If you created your Minipool via the One-Click launcher with ooNodz, then there is nothing you need to do! ooNodz will handle the BLS public keys and provide them to GoGoPool smart contracts, so your node will continue to validate the network with no interruptions.

### Other Node Providers

If you are hosting your node with a node provider, you must ask them for your node’s BLS Public Keys. They should be available somewhere in the provider’s node dashboard.

### Manual Minipools

If you are hosting a node yourself, you can use [this command](https://docs.avax.network/reference/avalanchego/info-api#infogetnodeid) to get your keys.

```bash
curl -X POST --data '{
    "jsonrpc":"2.0",
    "id"     :1,
    "method" :"info.getNodeID"
}' -H 'content-type:application/json;' 127.0.0.1:9650/ext/info
```

It should return something like this.

```bash
{
  "jsonrpc": "2.0",
  "result": {
    "nodeID": "NodeID-5mb46qkSBj81k9g9e4VFjGGSbaaSLFRzD",
    "nodePOP": {
      "publicKey": "0x8f95423f7142d00a48e1014a3de8d28907d420dc33b3052a6dee03a3f2941a393c2351e354704ca66a3fc29870282e15",
      "proofOfPossession": "0x86a3ab4c45cfe31cae34c1d06f212434ac71b1be6cfe046c80c162e057614a94a5bc9f1ded1a7029deb0ba4ca7c9b71411e293438691be79c2dbf19d1ca7c3eadb9c756246fc5de5b7b89511c7d7302ae051d9e03d7991138299b5ed6a570a98"
    }
  },
  "id": 1
}
```

The `publicKey` is your BLS Public Key, and `proofOfPossession` is your BLS Signature. Avalanche uses your public key as the signing message.

## For Safe Users

If you are a Gnosis Safe user, you must remain on the signing key page until a threshold of signers also signs, then it will complete. If you do not do this, your signature will never be verified, and your keys won't get updated on your Minipool, which will result being kicked off the network, as well as slashing!
