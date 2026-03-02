---
description: >-
  If your organization has multiple phone numbers set up in Daisychain, you can
  select which one is used as the default for outgoing messages.
icon: hashtag
---

# Phone Number Switching

### Why you might have multiple phone numbers

Organizations often use different numbers for different purposes — for example, one number for event recruitment, and one for general supporter outreach. Having multiple numbers lets your supporters keep those communications distinct and organized.

### The default number

Daisychain uses your **default phone number** as the sending number for new conversations and campaigns unless you specify otherwise.&#x20;

**To  change the default number:**

1. Go to **Settings > Channels > Texting**
2. Click the **Delivery Phone Numbers** tab
3. Find the number you want to make the new default
4. Click **Make default**

### How phone numbers work in active conversations

Phone numbers are "sticky" in most situations — once a conversation is started on a particular number, that number is preserved for follow-up messages, even if you later change the default.

**What counts as an active conversation?** If you've exchanged messages with a contact within the past week, Daisychain considers that conversation active and will continue using the same number. If it's been more than a week since the last message, the conversation is no longer considered active and the next message will go out from the current default.

### When the default number is always used (no stickiness)

There are three situations where Daisychain always uses the current default number, regardless of any prior conversation history:

* [**Campaigns**](campaigns/)**:** Each Campaign creates a fresh conversation per recipient. The sending number is whatever the default is at the moment the messages go out.
* [**Automations**](../organizing/automations/)**:** Messages sent automatically when a contact reaches a certain stage always use the current default.
* [**Flows:**](flows.md) Automated replies in that Flow use the current default, not the number the original broadcast came from.
