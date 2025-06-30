---
description: How to setup and use the Daisychain / ActBlue integration.
icon: sack-dollar
---

# ActBlue

**Setup**

To setup the ActBlue integration, visit **Settings > Integrations > ActBlue** and follow the on-screen instructions.&#x20;

**Importing Donors**

When you integrate your Daisychain and ActBlue account, people will automatically be imported into Daisychain when one of three things happens:

1. A new donation is made.
2. A recurring donation is cancelled.
3. A new refund is processed.

**ActBlue Automation Triggers**

You can trigger [automations](../organizing/automations/) when ActBlue donors make a donation, cancel a recurring donation, or process a refund. This makes it easy to follow up with donors as needed.

**ActBlue Message Campaigns**

If your account is integrated with ActBlue, you can choose "ActBlue Donations" [as a goal](../texting/campaigns/) when sending out a texting campaign. This will pre-populate your outgoing message with an `{{actblue_url}}` variable. Sending a message campaign with this variable which will ensure that recipients receive a unique link that enables:

* **Click and donation tracking**, providing real-time analytics on a per-recipient basis.
* **Pre-filling of ActBlue form**, saving donors from manually entering basic contact data that you have about recipients in Daisychain: name, email, phone number, address, etc.
