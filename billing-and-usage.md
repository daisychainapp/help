---
description: >-
  Everything you need to know about Daisychain invoices, payment methods, and
  how we handle billing.
icon: file-invoice-dollar
---

# Billing and Usage

### Billing and Usage

Your billing dashboard lives at **Settings > Account > Billing**. From there you can see a real-time estimate of your current bill, review recent invoices, manage payment methods and invoice recipients, and request tax exemption. A separate **Usage** tab provides a visual breakdown of messaging volume over time.

#### Upcoming Billing Period

The top of the Billing tab shows your current billing period and a live, itemized estimate of what your next invoice will look like. Daisychain bills on a monthly cycle, and this section updates as you send messages throughout the month.

The itemized table includes:

* **Platform Subscription** — your monthly subscription fee, with your tier shown in parentheses (e.g. Small, Medium, Large). Subscription fees don't apply to clients on a "texting only" plan.
* **SMS Segments** — total outbound SMS segments sent in the period, with a per-segment rate. Click the row to expand a day-by-day breakdown.
* **MMS Messages** — total outbound MMS messages sent in the period, with a per-message rate. Click the row to expand a day-by-day breakdown.
* **Add-ons** (when applicable) — custom URLs, concierge service, etc.
* **Account Credit** (when applicable) — any credits applied to the upcoming invoice, with a note explaining the reason.

The **Projected Total** at the bottom is your best estimate of the final invoice amount, including any credits and applicable taxes.

> Curious how SMS segments are counted? See [Understanding SMS Segments](texting/understanding-sms-segments.md).

#### Recent Invoices

Below the upcoming period, you'll see your three most recent invoices with date, amount, tax, and status (paid, open, etc.). Click **View** on any row to open the full invoice, or **View All** to see your complete invoice history.

#### Tax Exemption

If your organization has a valid state-issued tax-exemption certificate, click **Request tax exemption** to submit it for review. Once approved, sales tax will no longer be calculated on your invoices for the relevant jurisdictions.

#### Payment Method

Your current payment method appears at the bottom of the Billing tab. Click **Update** to change the card or bank account on file. This opens a secure window  where you can manage your payment details directly.

We currently support:

* Automatic bank debit (via ACH)
* Credit and debit cards
* Manual ACH transfers (preferred for large payments)

If you'd rather pay invoices manually instead of via auto-pay, email [billing@daisychain.app](mailto:billing@daisychain.app) to discuss options.

#### Invoice Recipients

Add or remove the email addresses that receive invoices and receipts directly from the Billing tab. You can have as many recipients as you need. Each recipient is tagged with their role:

* **Primary:** the main account contact. Receipts and account notifications go here.
* **Billing contact:** additional recipients who should receive invoices and receipts.

To add a recipient, type an email address in the **Add additional email** field and click **Add**. To remove one, click **Remove** next to their email.

#### Usage Tab

For a visual breakdown of messaging volume, navigate to **Settings > Account > Usage**. The Usage tab includes:

* A **Messages Sent** chart showing daily MMS and SMS volume over the past two months.
* A current-month **Usage Snapshot** with running totals for SMS Segments and MMS Messages.
* An **Export as CSV** option for downloading the underlying data.

For invoice estimates and itemized billing, use the Billing tab instead.

#### FAQ

**When are invoices sent?**

Daisychain sends invoices monthly. Each invoice covers your subscription fee for the upcoming month and any messaging usage from the previous month.

**How does auto-pay work?**

By default, we auto-charge the payment method on file and send both the invoice and receipt by email at the time of the charge.

**Will I get a receipt for my payment?**

Yes — receipts are sent automatically when your payment method is charged.

**How can I estimate my bill in advance?**

The Upcoming Billing Period section of the Billing tab shows a real-time itemized estimate of your current bill, including a daily breakdown of SMS and MMS usage.

**What's included in my invoice?**

Your monthly invoice may include:

* **Messaging Usage:** charges for outgoing SMS segments and MMS messages.
* **Subscription Fee:** monthly access to Daisychain's core organizing tools like [Pathways](https://daisychain.gitbook.io/help/organizing/pathways) and [Automations](https://daisychain.gitbook.io/help/organizing/automations). Some accounts will be on a "Texting Only" plan which has no subscription fee.&#x20;
* **Add-ons:** custom URLs, concierge service, etc.
* **Account Credit:** any credits that reduce the total.

**Why am I seeing small charges on an inactive account?**

If you're not actively sending campaigns but still see a small number of messages on your bill, the most likely cause is keyword auto-responses. Daisychain includes built-in keywords — HELP, START, and STOP — that are required for SMS compliance and can't be turned off. When anyone texts one of these words to your number, Daisychain automatically sends a reply, and that outbound message counts toward your usage.

If you've also configured custom keywords, those will fire too. Keywords always respond, regardless of whether you're running active campaigns or even logging into the platform.

To check whether keywords are the source, go to **Settings → Channels → Texting → Keywords** and review your active keywords. You can also check the **Usage** tab in your billing settings for a day-by-day breakdown, then cross-reference with your Inbox to see the actual conversations. For more on how keywords work, see Keywords.

**Questions?**

Reach us at [billing@daisychain.app](mailto:billing@daisychain.app). We're happy to help.
