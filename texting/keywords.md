---
description: >-
  Keywords let you automatically respond when someone texts a specific word to
  your number. You can use keywords to send an auto-reply message, trigger a
  Flow, or opt people in to receive messages from
icon: key
---

# Keywords

To manage keywords, go to **Settings → Channels → Texting → Keywords**.

### Built-in Keywords

Daisychain includes three built-in keywords required by [CTIA guidelines](https://www.ctia.org/the-wireless-industry/industry-commitments/messaging-interoperability-sms-mms) for SMS compliance. These keywords cannot be removed or modified.

#### HELP

Sends a help message with your organization's contact information. The response is automatically generated using your organization's name, website URL, and contact email from **Settings → Account**.

**Aliases:** help, info

#### START

Opts the person back in to receive text messages from your organization.

**Aliases:** start, unstop, subscribe

#### STOP

Opts the person out of receiving text messages from your organization. The STOP keyword also includes an **AI Auto Opt-Out** toggle. When enabled, Daisychain uses AI to detect and honor natural-language opt-out requests — even when they don't match a standard keyword. For more details, see Opt-Outs.

**Aliases:** stop, stopall, unsubscribe, cancel, end, quit

### Custom Keywords

Custom keywords let you define your own trigger words with custom responses. To create one, click **New Keyword** from the Keywords settings page.

#### Creating a Custom Keyword

**Keyword:** The word someone texts to trigger this keyword. Must be a single word with no spaces. Matching is case-insensitive.

**Keyword Aliases:** Optional additional words that also trigger this keyword. Click the **+** button to add aliases.

**Opts people in:** When enabled, texting this keyword will subscribe the person to receive messages from your account. For more on what "subscribed" means, see Subscription Statuses.

**Response Mode:** Choose one of the following:

* **Message:** Send a single auto-reply message. The response message composition box supports emoji and [variables for inserting personalized content](personalized-content/), including any standard or custom field.
* **Flow:** Start an automated conversation [Flow](flows.md). Select an existing Flow from the dropdown. You can use your Flow's instructions to control the first message sent.

#### Restrictions

You cannot create a custom keyword that matches any built-in keyword or alias. For example, you can't use "help," "stop," "subscribe," or any of the other built-in aliases as a custom keyword.

### How Keyword Matching Works

Keywords match when someone's **entire message** is just that keyword — a single word with nothing else. If someone sends a message that includes the keyword as part of a longer sentence, it will not trigger the keyword.

For example, if you have a keyword called **VOLUNTEER**:

| Incoming message    | Triggers keyword?        |
| ------------------- | ------------------------ |
| volunteer           | ✅ Yes                    |
| Volunteer           | ✅ Yes (case-insensitive) |
| VOLUNTEER           | ✅ Yes (case-insensitive) |
| I want to volunteer | ❌ No                     |
| Can I volunteer?    | ❌ No                     |

### What Happens When Someone Texts a Keyword

When someone texts a keyword to your number, a few things happen:

1. **A person is created** if one doesn't already exist for that phone number. The person will be marked as "Textable" — meaning you can send them messages. See [Subscription Statuses](subscription-statuses.md) for more details.
2. **If "Opts people in" is enabled,** the person is also marked as "Subscribed." This applies even if the person had previously opted out — texting a keyword with the opt-in toggle enabled will re-subscribe them.
3. **The auto-response is sent.** Either the configured message or the selected Flow is triggered.
4. **If the person is already opted in** and texts the keyword again, they will still receive the auto-response. This is by design — otherwise people might think the keyword isn't working.

### Things to Keep in Mind

**Keywords always fire, even during active conversations.** If someone is in an ongoing conversation with an organizer and their reply happens to be a single word that matches a keyword, the auto-response will be sent. This is important to consider when choosing your keywords.

For example, if you set up a keyword called **VOLUNTEER**, and an organizer asks someone "did you want to donate or volunteer?" — if that person replies with just "volunteer," the keyword auto-response will trigger. To avoid this, choose keywords that are unlikely to come up as natural single-word replies in a conversation, or use more distinctive words and phrases for your keywords (e.g., "VOL" instead of "VOLUNTEER").

**Keywords are account-wide.** All keywords apply to all phone numbers on your account.

**Built-in keywords take priority.** Custom keywords cannot override built-in keyword behavior.
