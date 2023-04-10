---
sidebar_position: 2
title: Authentication
sidebar_label: Authentication
description: Authentication
---

# Authentication

The Data API uses the same API key that you use to authenticate with other Stackup services.

To authenticate your requests, simply add a Stackup instance key to the
`su-access-key` header. As each instance key is scoped to a specific network,
the API results will return data within the same scope.
This ensures that you receive consistent and relevant data for your
intended network. While you can use the same instance key for both hosted
bundlers and data API access, if you require more granular access control,
we recommend creating a new instance solely for API access.
This approach allows for better management and control over the API usage and
associated resources.
