---
description: >-
  Daisychain automatically unsubscribes people who request to be opted-out by
  using certain keywords. You can also manually opt people out.
icon: octagon-xmark
---

# Opt-Outs

{% hint style="info" %}
**Need to import or export a list of of opt-outs?** You can do so by visiting Setttings > Channels > Opt-outs.&#x20;
{% endhint %}

### **Automatic Opt-Outs**

If someone sends a message using opt-out keywords (see below), that person will be automatically marked as opted out. This means that you will no longer be able to send that person another message through Daisychain unless they are opted back in.&#x20;

#### **Standard Opt-Out Keywords**

* CANCEL
* END
* QUIT
* STOP
* STOPALL
* UNSUBSCRIBE

#### **Non-Standard Opt-Out Keywords**

In addition to the standard keywords listed above, Daisychain will also opt out people who reply using variations and misspellings of these keywords, as well as a variety of hostile responses that clearly indicate that someone doesn't want to be messaged.

While Daisychain automatically process opt-outs for a variety of keywords (like "stop" and "unsubscribe"), it only does so when that word is the only word in a message in order to prevent "false-positives" — we don't want to accidentally opt someone out who wants to receive your messages.

### Manual Opt-Outs

You can also opt-out a person manually by clicking the "opt-out" button, which appears below their name in the [Inbox](inbox.md) and in their Profile.&#x20;

### Opting People Back In

#### **How to opt individual people in**

In the Inbox or a person's profile, hit the  `Opt In` button next to their phone number.

#### **How to opt people in via CSV**

1. **Prepare Your CSV**
   * Required columns:
     * `phone` (or `phone_number`)
     * `sms_opt_in` (set to `true` or `1`)
   * Optional: `first_name`, `last_name`, etc.
2. **Upload the CSV:** Go to **People → Import → CSV Upload**.
3. **Verify:** Spot Check a person’s profile.&#x20;
