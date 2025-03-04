---
icon: comment-sms
description: >-
  SMS messages are sent using blocks of characters, called segments -- and
  segments are how Daisychain calculates SMS usage for billing purposes.
---

# Understanding SMS Segments

A standard SMS message segment can have 160 "basic characters" -- which includes all [standard letters and numbers](https://en.wikipedia.org/wiki/GSM_03.38#GSM_7-bit_default_alphabet_and_extension_table_of_3GPP_TS_23.038_.2F_GSM_03.38). There are also "special characters" (like certain accented letters) might actually use up multiple characters in your segment. Emojis use a lot of characters, and change the number of characters allowed per segment in those messages to 70 instead of 160. Finally, if your message contains more than a single segment, subsequent segments have a limit of 153 characters. We know, it's a bit confusing.

**Daisychain will automatically do a few things to try to help with SMS segments:**

1. We will convert your outgoing multi-segment SMS message to an MMS message (which can contain 1600 plaintext characters) if it will save you money.
2. We will ensure that any multi-segment messages you send will be encoded in a way that most recipients with modern cell phones will receive them as a single message.​
3. We will automatically combine any incoming multi-segment messages that you might receive into a single message, for easy readability.&#x20;
4. When you create an [SMS campaign](https://help.daisychain.app/campaigns/campaigns), the message preview will display the number of segments in your message.

If you want to calculate exactly how many segments a message will use (including lots of nerdy details), you can head on over to this [SMS segment calculator.](https://twiliodeved.github.io/message-segment-calculator/)
