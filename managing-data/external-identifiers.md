---
description: >-
  Store IDs from other systems, like a voter file ID, so imports match on them
  and exports include them.
icon: fingerprint
---

# External Identifiers

An external identifier is an ID that a person has in another system, such as a state voter file ID or an L2 ID.

If you have an ID like this, store it as an external identifier rather than a [custom field](custom-fields.md).

{% hint style="info" %}
If your IDs are VAN IDs, don't upload them yourself. Connect the [NGP VAN integration](../integrations/ngpvan.md) and import your lists from there, and the VAN ID is attached to each person automatically.
{% endhint %}

Daisychain treats identifiers as a way to recognize a person, not just a piece of data about them, so:

* **Imports match on it.** When you import a CSV with the identifier mapped, people are matched by their ID first, so updates land on the right record even when a phone number or email has changed.
* **Exports include it.** The people export and the campaign exports (messages, replies and clicks) each get a column for every identifier, so you can match results back to your voter file.
* **The API can use it.** You can look up and match people by the identifier's API slug.

Identifiers from connected integrations, such as VAN or Action Network, are added automatically. You only need to create one yourself for IDs from a system we don't integrate with.

## Creating an external identifier

1. Go to **Settings**, then **People**, then **Fields**.
2. In the **External Identifiers** section, click **Add Identifier**.
3. Give it a name, for example "PA Voter ID".

## Filling it in

Import a CSV that has the ID column, along with phone or email:

1. Start a [CSV import](csv-imports.md) and map the ID column to your new identifier.
2. On the matching step, choose to match by the identifier.

If a row's ID doesn't match anyone yet, Daisychain falls back to matching by email or phone and attaches the ID to the person it finds. That means you can re-import your original list once to add IDs to people who are already in your account.

## Already using a custom field for IDs?

If your IDs are currently in a custom field, re-import them into an external identifier as described above. Once everyone has the identifier, you can stop mapping the custom field on future imports.

{% hint style="warning" %}
Deleting an external identifier removes that ID from everyone who has one, and imports can no longer match on it.
{% endhint %}
