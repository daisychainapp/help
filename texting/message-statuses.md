---
description: >-
  What each message status means, how a text moves from one status to the
  next, and how to see the delivery updates we get from the carrier for a
  single message.
icon: signal-bars
---

# Message Statuses

Every text Daisychain sends has a status. The status tells you where the message is right now: still waiting in Daisychain, handed off to our phone carrier partner, or confirmed delivered (or not) to the recipient's phone.

## The lifecycle of an outgoing message

Most messages follow this path:

**Pending → Accepted → Sending → Delivered**

1. **Pending.** The message has been created in Daisychain and is waiting to go out. Campaign messages sit here briefly while Daisychain works through the send queue.
2. **Accepted.** Daisychain has handed the message to our carrier partner and they have accepted it for delivery. From here on the message is out of Daisychain's hands.
3. **Sending.** The carrier partner has passed the message on to the recipient's mobile carrier (for example Verizon or T-Mobile) and is waiting to hear back. See ["Sending" Status](campaigns/understanding-the-sending-status-in-daisychain.md).
4. **Delivered.** The recipient's carrier confirmed the message reached the phone. This is the final status for a successful message.

After the message is accepted, every later status change comes from the carrier as a delivery update (a webhook). Carriers don't always send every update, so a message can skip a step, and occasionally updates arrive out of order.

### Statuses before a message is sent

These apply while a message is still in Daisychain and hasn't gone to the carrier yet.

| Status | What it means |
| --- | --- |
| **Pending** | Waiting to be sent. |
| **Deferred** | Held on purpose and scheduled to go out later. This happens during your account's quiet hours, or when a carrier's daily sending limit for your brand (currently T-Mobile's) has been reached. The expected send time is shown next to the message. Deferred messages go out automatically. |
| **Paused** | The campaign was paused before this message went out. See [Campaign Pausing](campaigns/campaign-pausing.md). |
| **Resumed** | The campaign was resumed and this message is back in line to send. |
| **Canceled** | Daisychain decided not to send the message, for example because the recipient opted out while it was deferred. |

### Statuses after a message is sent

These come from the carrier.

| Status | What it means |
| --- | --- |
| **Accepted** | Our carrier partner accepted the message. |
| **Queued** | The carrier partner has the message queued for sending. |
| **Sending** | On its way through the carrier network, waiting for a delivery receipt. |
| **Sent** | The recipient's carrier accepted the message but never sent back a delivery receipt. Many carriers don't send receipts in every case, so if a message stays in Sending without an update after an extended period has passed, we move it to Sent. Our carrier partners advise treating these messages as delivered to the phone, and reports count them as Delivered. A carrier update can still arrive later and change it. |
| **Delivered** | The recipient's carrier confirmed delivery. |
| **Undelivered** | The message was sent, but the recipient's carrier reported that it didn't reach the phone. Less certain than Failed; see [Failed and Undelivered](#failed-and-undelivered) below. |
| **Failed** | The message could not be sent. There is usually an error code; the reason is shown under the message in the conversation. See [Failed and Undelivered](#failed-and-undelivered) below. |
| **Expired** | The recipient's phone stayed off or out of service for so long that the carrier gave up trying to deliver the message. The message most likely never reached the phone, but the carrier doesn't confirm either way, so Daisychain reports it separately rather than as an error, and it doesn't count toward automatic campaign pausing. |

### Why a status can change later

Delivery updates from carriers are best effort. They don't always arrive, they can be late, and occasionally they arrive out of order. Daisychain shows its best current knowledge, so a message's status can keep changing for a few days after it was sent:

* **Sent isn't a failure.** It means the carrier accepted the message but no receipt came back. Sometimes the carrier partner tells us outright that it gave up waiting for a receipt; that also shows as Sent, not as an error. Our carrier partners advise treating Sent messages as delivered; we just can't confirm it.
* **Sent can become Expired.** When the recipient's phone was off or out of service for a long time, the carrier may report a few days later that it stopped trying. The message then moves from Sent to Expired.
* **Out-of-date updates are ignored where we can spot them.** If a stale update arrives after a message is already Delivered or Expired, Daisychain keeps the more informed status.

**Delivered**, **Undelivered**, **Failed**, **Canceled** and **Expired** are almost always final. Every other status can still change.

### Failed and Undelivered

These two statuses differ in how sure we can be:

* **Failed** means the message could not be sent. It never left our carrier partner, for example because the number isn't valid or the message was rejected before it went out. The recipient did not get it.
* **Undelivered** means the message was sent, but the recipient's carrier reported back that it didn't reach the phone. This is less certain. It rests on the carrier's report, and carrier reports are best effort:
  * **The reason is carrier-specific.** Every carrier reports problems in its own way. Some reports are precise, like "this person has opted out." Others are catch-alls: "carrier rejected the message" can mean a prepaid phone that has run out of credit, a line that isn't set up to receive that kind of text, or spam filtering, and the carrier doesn't tell us which.
  * **It's often temporary.** A phone that is switched off, a prepaid balance that runs out, or a carrier's filtering decision can cause one failure for a number that receives the next text just fine.
  * **Occasionally the report is wrong.** Our carrier partners have confirmed rare cases where a failure was reported for a message that was in fact delivered.

Not every carrier partner makes this distinction. Some report a rejection from the recipient's carrier as Failed rather than Undelivered. The error code shown under the message tells you where the failure came from, and a carrier rejection deserves the same caution whichever status it shows as.

Because of this, Daisychain only acts on a failure when the error is clear-cut, and doesn't stop texting someone because of one generic failure.

Some carrier errors also change the recipient's subscription. If the carrier tells us the number has opted out, Daisychain opts it out. If the carrier says it can't receive texts (a landline, for example), Daisychain opts it out for six months. If a number fails several times in a row as an invalid destination, which usually means it has been disconnected, Daisychain pauses texting it for seven weeks. See [Opt-Outs](opt-outs.md).

### Incoming messages

Replies from your contacts show as **Received**. They don't go through the delivery steps above.

## Seeing a message's delivery history

Admins and Managers can see the full status history of any single message, including every delivery update the carrier sent us:

1. Open the conversation, from the Inbox or from the person's profile.
2. Click the timestamp under the message (for example "2 hours ago"). For a deferred message, click the scheduled send time instead.
3. The message details open underneath. You'll see the current **Status**, the **From** and **To** numbers, whether it went as SMS or MMS, the number of segments, and who sent it.
4. The **Status log** below that lists each step with its exact time: when the message was created, when the carrier accepted it, and every delivery update after that. If an update came with a carrier error code, the code is shown next to it.

Click the timestamp again to hide the details.

The status log only shows updates from the carrier. Steps that happen inside Daisychain before a message is sent (Deferred, Paused, Resumed, Canceled) show up as the message's current status but aren't listed in the log. The automatic move from Sending to Sent after an extended period has passed also isn't listed, because it isn't a carrier update.

## Campaign totals

The [Campaign Report](campaigns/campaign-report.md), automation reports and the Deliverability page group these statuses into a few totals:

| Total | Includes |
| --- | --- |
| **Sending** | Pending, Accepted, Queued, Sending, Resumed |
| **Delivered** | Delivered and Sent |
| **Undelivered** | Undelivered, Failed and Canceled |
| **Expired** | Expired |
| **Paused** | Paused |
| **Deferred** | Deferred |

Sent counts as Delivered because our carrier partners advise treating those messages as having reached the phone. The Undelivered total is broader than the Undelivered status. It includes messages that couldn't be sent, messages the carrier reported as not delivered (see [Failed and Undelivered](#failed-and-undelivered)), and messages Daisychain canceled before sending.

When you filter people by "Undelivered" for a campaign, Expired messages are included too, since those recipients most likely never got the text. You can also filter people by the status of the campaign message they received (see [Filters](../managing-data/filtering-people.md)) or export message statuses (see [Exporting Data](../managing-data/exporting-data.md)).
