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
* Tags and messaging history from the secondary record will be discarded.
* Custom field values and CRM identifiers from integrated tools (i.e. VAN ID, Action Network ID) are carried over to the primary record only if the primary record’s field is empty (null). If multiple duplicate records contain values for the same custom field, no value will be merged, and the field will remain empty in the primary record after the merge.

## How Daisychain thinks about identity

A record in Daisychain represents a **person** — not an email address or a phone number. Contact details are evidence that two records might be the same person, but they aren't proof:

* **Households share phone numbers.** A parent and a teenager, or two spouses, often sign up for things with the same cell or landline number.
* **Organizations share inboxes.** Several staff members might all fill out forms with `hq@example.com` or `info@example.com`.
* **People share devices.** A volunteer might sign someone else up at a canvass using their own phone.

Because of this, Daisychain deliberately allows multiple people to exist with the same email address or phone number. If we forced every record with the same contact info into one person, everyone submitting from a shared phone or inbox would pile onto whichever person claimed it first — and their tags, custom fields, and message history would blend together in ways that are very hard to untangle.

The tradeoff runs in one direction on purpose: **an extra duplicate is easy to fix later** (that's what the Duplicate Manager is for), **but a wrong merge quietly corrupts both people's data**. So everywhere Daisychain has to decide whether two records are the same person, it errs on the side of keeping them separate unless the evidence agrees.

## How matching works

Whenever data enters Daisychain — a CSV import, an integration sync, a form submission, or an API call — we have to decide whether it belongs to a person you already have or to someone new. The decision works like this:

1. **Explicit IDs win.** If the incoming data carries a Daisychain person ID, or a CRM identifier from an integrated tool (like a VAN ID or Action Network ID) that you're matching on, that identifier is authoritative and email/phone matching is skipped.
2. **Email and phone find the candidates.** Otherwise, Daisychain looks for existing people who share any of the incoming email addresses or phone numbers.
3. **Names can veto a candidate.** A candidate whose first name clearly identifies a different person is not matched, even though they share an email or phone — Daisychain creates a new person instead. A submission for _Judith Smith_ on the same phone number as _John Smith_ is far more likely to be a spouse or family member than the same person.
4. **The best candidate wins.** A candidate who matches on both the incoming email _and_ phone number beats one who matches on only one of them. If candidates are still tied, the one whose name most closely resembles the incoming name is chosen.
5. **No plausible candidate means a new person.** If nothing matches — or every candidate was vetoed by the name check — Daisychain creates a new person.

### The name check is forgiving

The name check only rejects a match when both first names are present and show _no_ agreement at all. Any of these signals keeps the match:

* **Exact match** after normalization — capitalization, accents, and generational suffixes like `Jr.` are ignored.
* **Nicknames** — `Bill` matches `William`, and `Rob` matches `Bob` (both are nicknames of Robert).
* **Phonetic matches** — homophones like `Geoffrey` and `Jeffrey` sound alike and match.
* **Minor typos** — small spelling differences like `Jonh` and `John`.
* **Initials** — `J` matches `John`.
* **A blank first name** on either record never blocks a match.

Last names alone never veto a match: people change surnames (through marriage, for example) far more often than first names, so `Jane Smith` still matches `Jane Jones` at the same email address. Hyphenated surnames match on either part — `Smith-Jones` matches `Smith`.

## How this shapes duplicate suggestions

The Duplicate Manager applies the same thinking in reverse. It looks for people in your account who share an email address or phone number, and then runs the same name check before suggesting a merge:

* Two records that share contact info and have compatible names (including nicknames, typos, and phonetic matches) **are suggested** as duplicates for you to review.
* Two records that share contact info but have clearly different first names — the John and Judith case — **are not suggested**, because they're almost certainly different people who happen to share a phone or inbox.

{% hint style="info" %}
Merging is permanent and, as described above, discards some data from the secondary record. That's why Daisychain suggests duplicates for your review rather than merging automatically — you know your list best, and only you can tell whether two plausible-looking records really are the same person.
{% endhint %}
