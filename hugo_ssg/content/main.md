---
weight: 10
title: API Reference
---

# Introduction

Welcome to the **FundedYouth API**! You can use our API to access FundedYouth endpoints, which allow interaction with our public tools and resources for hands-on STEM education, prototyping, and on-demand manufacturing programs.

The API is currently in development and will include authentication and authorization. Once implemented, it will support:

- `Authorization: Bearer <token>`
- `X-API-Key: <key>`

We provide code examples in **cURL, PHP, Python, Fetch, and Axios**. You can view code examples in the dark area to the right and switch programming languages using the tabs in the top right.

**This documentation was created for the FundedYouth API using a markdown-based reference style.**

## Notification Types

<aside class="success">Success</aside>
<aside class="notice">Notice / Info</aside>
<aside class="warning">Warning / Error</aside>

## Environment Variables

| Environment       | Base URL                  |
| ----------------- | ------------------------- |
| {{ Development }} | `http://localhost`        |
| {{ Production }}  | `https://fundedyouth.org` |

**Endpoint**: `{{ base_url }} /api`

All API endpoints are relative to this base URL.

<aside class="notice">
Authentication is required for all protected endpoints. You will receive an API token and key once your account is authorized.
</aside>
