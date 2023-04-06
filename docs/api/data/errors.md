---
sidebar_position: 5
title: Errors
sidebar_label: Errors
description: Errors
---

Approriate HTTP status codes will be returned along with an `Error` object response for context.

Possible HTTP status codes

| Status Code | Description                                                                              |
| ----------- | ---------------------------------------------------------------------------------------- |
| 200         | Everything worked as expected.                                                           |
| 400         | The request was rejected due to a malformed or missing parameter.                        |
| 401         | API key is not valid.                                                                    |
| 403         | API key does not have permission to make the request.                                    |
| 429         | Your request was denied because you have exceeded the rate limit for your API key.       |
| 500         | Something went wrong at the Stackup server. We've been notified and are looking into it. |

### Returns

```json
{
  "error": {
    "message": "Everything worked as expected."
  }
}
```
