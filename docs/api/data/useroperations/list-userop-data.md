---
sidebar_position: 2
title: List all UserOperations
sidebar_label: List all UserOperations
description: List all UserOperations
---

Returns a list of [UserOperation data objects](./the-useropdata-object).

### Endpoint

```
GET /v1/useroperations
```

### Parameters

##### **`sender`** - optional string

Sender address.

---

##### **`bundler`** - optional string

Bundler address.

---

##### **`paymaster`** - optional string

Paymaster address.

---

##### **`entryPoint`** - optional string

Entrypoint address.

---

##### **`transaction_hash`** - optional string

Transactions hash.

---

##### **`useroperation_hash`** - optional string

User operation hash.

---

##### **`from`** - optional string

Date in UTC `ISO 8601` format. requires `to` parameter.

---

##### **`to`** - optional string

Date in UTC `ISO 8601` format. requires `from` parameter.

---

##### **`sponsored`** - optional boolean

Filter by sponsored user ops.

---

##### **`success`** - optional boolean

Filter user ops that have succeeded or failed.

---

### Returns

A hash with a data property that contains an array [UserOperation data objects](./the-useropdata-object.md).

```json
{
  "data": [
    {
      "userOperation": {
        "sender": "0x3C003eEA3F17f8ae53d3358563D9820E9b05602D",
        "nonce": "0x0",
        "initCode": "0x",
        "callData": "0xb61d27f6000000000000000000000000d4e5aa212d7b9cd781e0708b5a3764c949e4ce9500000000000000000000000000000000000000000000000000005af3107a400000000000000000000000000000000000000000000000000000000000000000600000000000000000000000000000000000000000000000000000000000000000",
        "callGasLimit": "0x9a7f",
        "verificationGasLimit": "0x186a0",
        "preVerificationGas": "0xb708",
        "maxFeePerGas": "0x4a16acc2",
        "maxPriorityFeePerGas": "0x4a16aca4",
        "paymasterAndData": "0x",
        "signature": "0x41b6d45c2ffcc7c798095fa71fcab913ff20a183d730946283f1d3584c3fb76b12c985888560e0dbeea7fcfbf174f8326c0f28544e2cbdd203bddd3a0bc70adf1b"
      },
      "userOpHash": "0xb3ce4f1fdcfb62026400600ed22f765eed4e10dad6fd2e98bcc9448eca38b31b",
      "sender": "0x3c003eea3f17f8ae53d3358563d9820e9b05602d",
      "paymaster": "0x0000000000000000000000000000000000000000",
      "nonce": "0x0",
      "success": true,
      "reason": null,
      "actualGasCost": "0x616691280e97",
      "actualGasUsed": "0x1508d",
      "bundler": "0x9c98b1528c26cf36e78527308c1b21d89baed700",
      "blockNumber": 33093730,
      "entryPoint": "0x0576a174D229E3cFA37253523E645A78A0C91B57",
      "blockHash": "0xaacb1ee5d5c36c223fc42d6720ddb5ca0e6771223f18f8421debf71d5c7cdff5",
      "created": 1673961900
    }
  ]
}
```
