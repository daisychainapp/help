---
description: Find matching email and phone records and merge people.
icon: people-pants
---

# Deduplication

To access the Duplicate Manager, navigate to **Settings > People > Duplicates**

You can identify duplicate records in your account based on matching emails or phone numbers. Once identified, you can can review the suggested duplicates and merge them to keep your data clean and organized.

**Here’s what happens when you merge records:**

* The “primary” record (indicated with a > symbol next to it) is preserved, and “secondary” record(s) are deleted.
* Additional emails, phone numbers, and addresses from secondary records will be appended to the the primary record.
* Tags, and messaging history from the secondary record will be discarded.
* Custom field values and CRM identifiers from integrated tools (i.e. VAN ID, Action Network ID) are carried over to the primary record only if the primary record’s field is empty (null). If multiple duplicate records contain values for the same custom field, no value will be merged, and the field will remain empty in the primary record after the merge.

