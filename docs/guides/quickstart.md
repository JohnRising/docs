---
sidebar_position: 1
image: https://i.imgur.com/N6pe40z.png
title: ERC-4337 Quickstart Guide
sidebar_label: Quickstart
description: This tutorial walks through a basic implementation of a smart contract wallet using ERC-4337, a proposal for account abstraction for Ethereum.
---

# Quickstart

Explore a basic implementation of account abstraction using ERC-4337. This example will create an account and initiate a transaction on the Ethereum Goerli testnet.

If you are new to account abstraction, we recommend the [introduction to account abstraction](/docs/introduction/account-abstraction) and an [overview of ERC-4337](/docs/introduction/erc-4337-overview).

:::warning
The video uses an old version of the examples repo. Follow the written instructions below the video. Use the video for informational purposes only.
:::

<div align="center" width="100%" class="video"><iframe width="100%" height="100%" src="https://www.youtube.com/embed/zvnm2GnMAts" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div>

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

Deposit ETH into the account on Goerli.

Navigate to a faucet, such as https://goerlifaucet.com/. Enter the account address and claim the testnet ETH.

:::info

Faucets do not send directly to smart contracts. You must deposit ETH or ERC-20 tokens from the faucet before your first transaction.

:::

## 6. Initiate the transfer

The `simpleAccount transfer` command allows you to transfer ETH from the smart contract account to any address. It will create a user operation, sign it, and send it to the bundler:

```
yarn run simpleAccount transfer --to <address> --amount <eth>
```

You can then find the transaction using a block explorer like [etherscan](https://goerli.etherscan.io/).

### Troubleshooting

While using this quickstart example, you may encounter these common error messages.

- `AA21 didn't pay prefund` is an error from the bundler that indicates that the account does not have enough funds. This usually means that you did not fund your account in step 5.

- `400 bad request: invalid tracer value` or `This method is not whitelisted` are responses that you may get if you are running your own bundler locally and using an external node provider. Most node providers do not support the custom tracing that bundlers need. Either run your own local node or use Stackup's bundler service.

- `entryPoint: Implementation not supported` means that the bundler being used for the transaction does not support the selected Entry Point. If you are using a Stackup bundler, we recommend setting your bundler instance to the latest version and the canonical Entry Point contract.

## Next Steps

You've successfully sent a transaction using a smart contract account and ERC-4337! Now that you've done a simple transfer with your account, you can begin working with ERC-4337.

Here are some things for you to explore:

- Try sponsoring a transaction with the [Paymaster Example](/docs/guides/paymaster-example)
- Read the code in the quickstart repository and see some more examples:
  - [Transfer ERC-20 tokens](https://github.com/stackup-wallet/erc-4337-examples#transfer-erc-20-token)
  - [Batch transfer ETH](https://github.com/stackup-wallet/erc-4337-examples#transfer-erc-20-token)
  - [Batch transfer ERC-20 tokens](https://github.com/stackup-wallet/erc-4337-examples#transfer-erc-20-token)
- Explore some account contract samples developed by the Ethereum Foundation on [GitHub](https://github.com/eth-infinitism/account-abstraction/tree/develop/contracts/samples)
- Showcase your ERC-4337 account with the [Trampoline](https://github.com/plusminushalf/trampoline-example/tree/fingerprint) chrome extension template.
- See this [list of more account abstraction resources](/docs/introduction/more-resources).
- Explore third party SDKs, such as:
  - [ZeroDev](https://www.zerodev.app/), a smart contract wallet framework that greatly simplifies the implementation of smart contract accounts for wallets and dapps. View their [getting started guide](https://docs.zerodev.app/getting-started) to create an example React app.

### Wondering what account abstraction means for your company?

You may be interested in a [Discovery package](https://www.stackup.sh/discovery).
