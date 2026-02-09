---
description: You can easily export data in your Daisychain account.
icon: arrow-down-from-line
---

# Exporting Data

## Exporting People Data

You can easily export data stored in Daisychain from the People section as CSV files. Here's how:

* Navigate to the **People** section.
* Optionally, [filter your list](https://help.daisychain.app/filtering-people) if you only want to export a subset of your people. (Note that selecting people using checkboxes will not affect who does/doesn't get exported.)

Hit the three dots, and press the "Export" link, and a CSV file will be generated and emailed to you.

![](https://44727351.fs1.hubspotusercontent-na1.net/hubfs/44727351/image-png-Oct-30-2024-12-59-20-9046-AM.png)

Exported CSVs will include columns for:

* A Daisychain ID #
* All [standard fields](https://help.daisychain.app/filtering-people)
* All custom fields
* Tags
* Date created
* Date updated
* Latitude and Longitude
* SMS Fields
  * sms\_subscribed
  * sms\_subscribed\_at
  * sms\_subscription\_source\_kind
  * sms\_opt\_out\_at
  * sms\_opt\_out\_reason
* Email Fields
  * email\_subscribed
  * email\_subscribed\_at
  * email\_subscription\_source\_kind
  * email\_opt\_out\_at
  * email\_opt\_out\_reason

## Exporting Message Data

You can export your account's SMS message history and opt-out list as CSV files. To access these exports, navigate to **Settings > Account > Exports**.

You'll see two export options:

### **All SMS Messages**

A complete export of all incoming and outgoing SMS messages for your account. Click the button to generate a CSV file, which will include the following columns:

* `id` — Unique message ID
* `conversation_id` — The conversation the message belongs to
* `direction` — Whether the message is `incoming` or `outgoing`
* `status` — Delivery status (e.g., `delivered`, `undelivered`)
* `error_code` — Error code, if applicable
* `external_id` — The message ID from the carrier
* `from` — The sending phone number
* `to` — The receiving phone number
* `body` — The message content
* `segment_count` — Number of SMS segments
* `billing_kind` — Whether the message was billed as `sms` or `mms`
* `phone_number_type` — The recipient's phone type (e.g., `mobile`)
* `carrier_name` — The recipient's carrier
* `broadcast_name` — The name of the campaign, if the message was part of one
* `broadcast_id` — The campaign ID, if applicable
* `opt_out_reason` — If the message triggered an opt-out, the reason
* `person_id` — The Daisychain person ID associated with the message
* `card_id` — The card ID, if applicable
* `automation_execution_id` — The automation execution ID
* `automation_id` — The automation ID, if applicable
* `accepted_at` — When the message was accepted by the carrier
* `created_at` — When the message was created

### **SMS Opt Outs**

A list of all phone numbers currently opted out of receiving SMS messages from your account. This CSV includes:

* `phone_number` — The opted-out phone number
* `created_at` — When the opt-out was recorded

***

Let me know if you want any adjustments to the tone, level of detail, or structure.
