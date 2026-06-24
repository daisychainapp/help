---
description: You can easily export data in your Daisychain account.
icon: arrow-down-from-line
---

# Exporting Data

## Exporting People Data

You can easily export data stored in Daisychain from the People section as CSV files. Here's how:

* Navigate to the **People** section.
* Optionally, [filter your list](https://help.daisychain.app/filtering-people) if you only want to export a subset of your people. (Note that selecting people using checkboxes will not affect who does/doesn't get exported.)

Click the three dots, and select the "Export" link, and a CSV file will be generated and emailed to you.

![](https://44727351.fs1.hubspotusercontent-na1.net/hubfs/44727351/image-png-Oct-30-2024-12-59-20-9046-AM.png)

Exported CSVs will include columns for:

* A Daisychain ID #
* All [standard fields](https://help.daisychain.app/filtering-people)
* All custom fields
* Tags
* Date created
* Date updated
* Latitude and Longitude

**SMS subscription fields**

- sms_subscribed — True/false. true means the contact has an active SMS subscription (they have a subscribed date and haven't opted
  out). false means they're either not subscribed or have opted out.
- sms_subscribed_at — The date/time the SMS subscription was created.
- sms_subscription_source_kind — How the SMS subscription came to be. Common values: data_entry (added by hand in Daisychain), upload
  (CSV import), web (a web form), sms (they texted in / replied), api, merge (created when two records were merged), or the name of the
  integration it came from (actblue, actionnetwork, everyaction, controlshift, mobilize_america, fundraise_up).
- sms_opt_out — True/false flag for whether the contact is currently opted out of SMS.
- sms_opt_out_reason — Why they're opted out. Values include manual (opted out by a team member), automatic sms stop, they texted STOP and the carrier processed it), ai_auto_opt_out (our
  AI detected an opt-out request in their reply), invalid_phone / invalid_phone_type (the number isn't textable, e.g. a landline),
  phone_opt_out, or upload (marked opted out in an import).
- sms_opt_out_at — The date/time the opt-out was recorded.

**Email subscription fields**

- email_subscribed — True/false, same logic as SMS: an active email subscription with no opt-out.
- email_subscribed_at — The date/time the email subscription was created.
- email_subscription_source_kind — How the email subscription was created.
- email_opt_out_at — The date/time of the email opt-out (blank if they haven't opted out).
- email_opt_out_reason — Why they're opted out of email — typically email_click (clicked unsubscribe), email_bounce (the address
  bounced), email_spam (marked as spam), manual, or upload.

A couple of things worth noting: the *_at and *_reason fields are only populated when that event actually happened, so a blank just
means it doesn't apply (e.g. an empty sms_opt_out_at means they haven't opted out). And "subscribed" is always derived from having a
subscription date and no opt-out — so it's the quickest single column to look at for "can I currently contact this person."

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
