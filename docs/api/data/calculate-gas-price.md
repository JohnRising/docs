---
sidebar_position: 9
title: Total Gas Sponsored
sidebar_label: Gas
description: Calcualte Gas Sponsored
---

Returns the total sponsored gas in USD. One of `sender`, `bundler` or `paymaster` parameter are required.

### Endpoint

```
GET /v1/calculate-gas-sponsored
```

### Parameters

##### **`sender`** - required if `paymaster` or `bundler` are undefined - string

Sender address.

---

##### **`paymaster`** - required if `sender` or ` bundler` are undefined - string

Paymaster address.

---

##### **`bundler`** - required if `sender` or `paymaster` are undefined - string

Bundler address.

---

##### **`from`** - optional string

Date in UTC `ISO 8601` format. requires `to` parameter.

---

##### **`to`** - optional string

Date in UTC `ISO 8601` format. requires `from` parameter.

---

### Returns

A hash with a data property that contains a `totalGasCost` property containing
the calculated total sponsored gas cost and a `transactions` property that contains a list of transactions.

```json
{
  "data": {
    "totalGasCost": {
      "wei": 1037949509521002,
      "converted": {
        "currency": "USD",
        "amount": "1.9732873305306384289"
      }
    },
    "transactions": [
      {
        "sender": "0xdD1eD4e1806AC09A7e44E34E6cdb7F365e86BfBD",
        "gasCost": 219246357693168,
        "userOpHash": "0x53e0767595eac41a5903d789008b689f3b4ff4dd23baefaf97213c488340916b"
      },
      {
        "sender": "0xdD1eD4e1806AC09A7e44E34E6cdb7F365e86BfBD",
        "gasCost": 818703151827834,
        "userOpHash": "0x178f4f6cb894522428b05d4129decadff65c3be1d608b3fe573dc388e37319b4"
      }
    ]
  }
}
```
