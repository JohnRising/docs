---
sidebar_position: 4
title: Pagination
sidebar_label: Pagination
description: Pagination
---

# Introduction

Pagination is applied to all List API requests in the UserOperations API,
allowing you to efficiently manage and retrieve data in smaller chunks.
When you make a List API request, you can expect to see a `meta` key in the
response body containing relevant pagination parameters.

Here's a brief description of each pagination parameter:

| Parameter    | Description                                                                        |
| ------------ | ---------------------------------------------------------------------------------- |
| page         | The current page number being displayed.                                           |
| limit        | The number of records displayed per page.                                          |
| totalRecords | The total number of records available in the dataset.                              |
| totalPages   | The total number of pages available based on the given "limit".                    |
| link         | A URL to the next page of results. `null` will be returned if it is the last page. |

To customize the number of records returned per page, you can adjust the
`limit` parameter. The maximum limit is 100 records per page,
while the default is 25.
