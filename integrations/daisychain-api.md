---
description: Build your own integrations with the Daisychain API.
icon: code
---

# Daisychain API

The Daisychain API lets your developers connect Daisychain to your own tools. You can use it to add people and record actions, manage tags, subscriptions, and contact details, read broadcasts and conversations, build Flows, and more.

### API Documentation

The full reference, with every endpoint and example requests, is at [go.daisychain.app/api-docs](https://go.daisychain.app/api-docs/). You can try requests directly from that page.

### API Keys

Admins can create API keys at **Settings > API Keys**. A key's credentials are only shown once, when it's created. If you lose them, reset the key to get new ones.

Send the key in the `X-API-Token` header of each request. Every key has full access to the API for its account, so store it somewhere safe.

### Recording Actions

The **Create an action and person** endpoint (`POST /api/v1/actions`) records something a person did in another system, like a form submission. It creates or updates the person, matching them against people already in your account (see [Deduplication](../managing-data/deduplication.md)), and it can trigger [automations](../organizing/automations/). You can [filter those automations](../organizing/automations/filtering-automations.md) on the details you send.

### Data Dictionary

The [Data Dictionary](https://go.daisychain.app/api-docs/data-dictionary) documents the tables available through [Data Sync](../managing-data/data-sync.md), including column types, relationships, and enum values. You can also download it as [JSON](https://go.daisychain.app/api-docs/data-dictionary/json) or [DDL](https://go.daisychain.app/api-docs/data-dictionary/ddl).
