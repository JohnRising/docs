---
sidebar_position: 3
title: Retrieve a UserOperation
sidebar_label: Retrieve a UserOperation
description: Retrieve a UserOperation
---

# Retrieve a UserOperation

Returns a [UserOperation data object](./the-useropdata-object).

### Endpoint

```
GET /v1/useroperation/:useropHash
```

### Parameters

No parameters.

### Returns

Returns a list of `UserOperation log` objects. If the call fails it returns an `Error` object.

```json
{
  "data": [
    {
      "address": "0x0576a174d229e3cfa37253523e645a78a0c91b57",
      "topics": [
        "0x49628fd1471006c1482da88028e9ce4dbb080b815c9b0344d39e5a8e6ec1419f",
        "0xb3ce4f1fdcfb62026400600ed22f765eed4e10dad6fd2e98bcc9448eca38b31b",
        "0x0000000000000000000000003c003eea3f17f8ae53d3358563d9820e9b05602d",
        "0x0000000000000000000000000000000000000000000000000000000000000000"
      ],
      "data": "0x000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000010000000000000000000000000000000000000000000000000000616691280e97000000000000000000000000000000000000000000000000000000000001508d",
      "blockNumber": "0x1f8f862",
      "transactionHash": "0xaf386bde2e38ef72c48e94e173181539ebcead3791d460159fc43cdeb02af665",
      "transactionIndex": "0x3",
      "blockHash": "0xaacb1ee5d5c36c223fc42d6720ddb5ca0e6771223f18f8421debf71d5c7cdff5",
      "logIndex": "0x8",
      "removed": false
    }
  ]
}
```
