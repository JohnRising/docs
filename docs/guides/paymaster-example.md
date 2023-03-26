---
sidebar_position: 2
image: https://i.imgur.com/N6pe40z.png
title: Paymaster Quickstart Guide
sidebar_label: Paymaster Example
description: This example walks through a basic implementation of using a paymaster to sponsor gas fees with ERC-4337, a proposal for account abstraction for Ethereum.
---

# Paymaster Example

This example expands on the [Quickstart Example](/docs/guides/quickstart) to sponsor gas fees using ERC-4337 and Stackup's [Paymaster API](/docs/api/paymaster/introduction).

If you just completed the quickstart example, you can skip to [step 6](#6-subscribe-to-a-developer-plan).

<div align="center" width="100%" class="video"><iframe width="100%" height="100%" src="https://www.youtube.com/embed/XxVVR1ppbHY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div>

## 1. Download

Clone the [ERC-4337 Examples](https://github.com/stackup-wallet/erc-4337-examples) repository to download the scripts.

```
git clone https://github.com/stackup-wallet/erc-4337-examples.git
```

## 2. Install

This example uses the [Infinitism](https://github.com/eth-infinitism/account-abstraction) package created by the ERC-4337 core developers. Install it, and all other dependencies.

```
yarn install
```

## 3. Initialize your configuration

You can now initialize your local configuration.

```
yarn run init
```

A `config.json` file will be created. The file will look like this:

```
{
  "bundlerUrl": "http://localhost:4337",
  "rpcUrl": "http://localhost:8545",
  "signingKey": "0x...",
  "entryPoint": "0x...",
  "simpleAccountFactory": "0x...",
  "paymasterUrl": ""
}

```

If you are not running a local [bundler](https://github.com/stackup-wallet/stackup-bundler) or network node, you will need to set a `bundlerUrl` and `rpcUrl`.

You can create a free bundler instance at [app.stackup.sh](https://app.stackup.sh/sign-in). In this example, select the Ethereum Goerli network for the instance and ensure the version is set to `0.4.0`. Once the instance is created, copy the instance URL and replace the default `bundlerUrl` with the generated address.

![Copy the bundler instance URL from the Stackup app](../../static/img/copy-bundler-url.png)

You also need to set the `rpcUrl`. Set the `rpcUrl` to the same url as the `bundlerUrl`. Stackup's bundler also runs a full node, so you can send any normal RPC requests to it as well. If you want to use a different endpoint, `rpcUrl` can be set to any network node.

Your `config.json` fill will now look like this:

```
{
  "bundlerUrl": "https://node.stackup.sh/v1/rpc/...",
  "rpcUrl": "https://node.stackup.sh/v1/rpc/...",
  "signingKey": "0x...",
  "entryPoint": "0x...",
  "simpleAccountFactory": "0x..."
  "paymasterUrl": ""
}

```

## 4. Create an account

Create an account using the factory `simpleAccountFactory` defined in the configuration file.

```
yarn run simpleAccount address
```

An address will be returned. At this point, the smart contract account has not been deployed.

## 5. Fund the account

Deposit an ERC-20 token into the account on Goerli.

Navigate to an ERC-20 faucet, such as https://faucet.polygon.technology/. Enter the account address and claim the testnet ERC-20 token.

## 6. Subscribe to a developer plan

To sponsor a transaction, you will need to upgrade to the Developer plan in your [Stackup dashboard](https://app.stackup.sh/dashboard). Do this now.

All commands in the example folder have a `--withPaymaster` flag. This will send your user operations to the `paymasterUrl` specified in your config. If you are using Stackup's paymaster, the `paymasterUrl` API key will be the same as the `bundlerUrl` but at the paymaster endpoint.

For example, if `bundlerUrl` is:

```
"bundlerUrl" = "https://node.stackup.sh/v1/rpc/<API key>"
```

Then your `paymasterUrl` is:

```
"paymasterUrl" = "https://app.stackup.sh/api/v2/paymaster/payg/<API key>"
```

Regardless of whether you use Stackup's paymaster service or not, the endpoint is expected to implement a standard [JSON-RPC interface](../api/paymaster/rpc-methods) and return back a `paymasterAndData` field if it agrees to sponsor your transaction.

## 7. Send a sponsored transaction

The `simpleAccount erc20Transfer` command allows you to transfer ETH from the smart contract account to any address. It will create a user operation, sign it, and send it to the bundler:

```
yarn run simpleAccount erc20Transfer --token <address> --to <address> --amount <decimal>
```

Set the `--token` address to the address of the ERC-20 token. You can get this address from a block explorer like [etherscan](https://goerli.etherscan.io/). The `--to` address is the address you will send the tokens to, and set `--amount` to the number of ERC-20 tokens you want to transfer.

Once the transaction is sent, you can check a block explorer like [etherscan](https://goerli.etherscan.io/).

### Troubleshooting

Here are some error codes you may experience if you are using the quickstart example repository and a paymaster:

- `invalid userOp or paymaster signature` means that signature verification failed. While using a paymaster, this usually means that the user operation has changed after the `paymasterAndData` or `signature` fields have been set. Make sure nothing changes between paymaster approval and signing.

- `paymaster: not enough deposit to cover max prefund` means that the Paymaster contract does not have enough funds deposited with the Entry Point. If this occurs while using Stackup's paymaster, please contact us immediately in Discord by tagging @Stackup Team or email founders@stackup.sh.

- `AA21 didn't pay prefund` is an error from the bundler that indicates that the account does not have enough funds. If you intended to use a paymaster, this usually means that the `--withPaymaster` flag was not set so the `paymasterAndData` field of the user operation was empty when it was sent to the bundler.

- `400 bad request: invalid tracer value` or `This method is not whitelisted` are responses that you may get if you are running your own bundler locally and using an external node provider. Most node providers do not support the custom tracing that bundlers need. Either run your own local node or use Stackup's bundler service.

- `entryPoint: Implementation not supported` means that the bundler being used for the transaction does not support the selected Entry Point. If you are using a Stackup bundler, we recommend setting your bundler instance to the latest version and the canonical Entry Point contract.

## Next Steps

You've successfully sent a transaction using a smart contract account and ERC-4337! You are now ready to go out and build your own application with ERC-4337.

Wondering what account abstraction means for your company? You may be interested in a [Discovery package](https://www.stackup.sh/discovery).
