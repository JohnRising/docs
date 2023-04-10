---
sidebar_position: 3
title: API Rate Limits
sidebar_label: API Rate Limits
description: API Rate Limits
---

Our API imposes rate limits to ensure fair usage and maintain the stability of our service. The rate limits vary depending on your subscription tier and are set based on the number of requests per second (req/s).

#### Rate Limits by Subscription Tier.

| Subscription Tier | Rate Limit       |
| ----------------- | ---------------- |
| Free              | 5 requests/sec.  |
| Developer         | 10 requests/sec. |
| Enterprise        | Contact us.      |

#### Free Tier

The Free Tier is limited to 5 requests per second. This tier is suitable for users who are just getting started with our API or require a low volume of requests.

#### Developer Tier

The Developer Tier has a rate limit of 10 requests per second. This tier is designed for users who need more capacity and faster access to the API.

#### Enterprise Tier

For Enterprise customers who require a custom rate limit, please contact us.

### Exceeding Rate Limits

If you exceed your subscription's rate limit, the API will return a `429` Too Many Requests HTTP response status.
