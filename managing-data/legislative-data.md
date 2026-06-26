---
description: >-
  How Daisychain looks up each person's elected officials and how you can filter,
  view, and message based on legislative districts.
icon: landmark-dome
---

# Legislative Data

Daisychain automatically determines which elected officials represent each person in your database, based on their address. Once a person's address is geocoded, you can:

* **Filter** your audience by congressional district.
* **Insert** a person's legislators directly into text messages and Charms.
* **View** a person's legislators on their profile.

{% hint style="info" %}
Legislative lookups are based on each person's **address**. For the lookup to work, the person must have an address on file — at minimum a **ZIP code**, though a full street address produces the most accurate results.
{% endhint %}

### What Data Daisychain Stores

Daisychain maintains a database of **current US federal legislators** — the US House of Representatives and the US Senate. This data is sourced from the public-domain [`unitedstates/congress-legislators`](https://github.com/unitedstates/congress-legislators) project, US Census district boundaries, and official Congressional photos, and is refreshed regularly.

For each legislator, Daisychain stores information such as:

* **Name and party** — full name, first/last name, and party affiliation.
* **Position and district** — the office they hold (e.g., US House Representative, US Senator) and the district or state they represent.
* **Contact details** — office phone, fax, official website, and contact-form URL.
* **District offices** — physical office locations with addresses, phone numbers, and hours.
* **Social accounts** — Twitter/X and Facebook handles.
* **Photo** — an official portrait.
* **Senate specifics** — for senators, their class and junior/senior rank within the state.

Daisychain also stores the **district boundaries** (congressional district shapes and state outlines) used to match a person's address to the right representatives.

{% hint style="info" %}
Coverage today is **US federal** — the US House and US Senate. The underlying system is built to support additional legislatures over time.
{% endhint %}

### How a Person Is Matched to Their Legislators

When a person's address is added or updated, Daisychain geocodes it and resolves which districts they fall into:

* **Full street addresses** are matched to a precise point and placed inside the correct congressional district boundary (point-in-polygon).
* **Less precise addresses** (e.g., ZIP code only) fall back to a likelihood-based match — Daisychain picks the most probable district for that postal code.
* **State-only addresses** can still resolve US Senators (which are statewide), but not a specific House district.

Because matching happens when the address is saved, a person's district membership is precomputed and ready to use for filtering and messaging.

### Filtering by Congressional District

You can build an audience of everyone in a given congressional district:

1. Go to the **People** section and press **Filter**.
2. Choose the **Legislative District** filter category.
3. Select the **Country**, optionally narrow by **State**, then choose the **Legislature** (e.g., US House) and the specific **District**.
4. Choose whether people should be **in** or **not in** that district.

The filter matches against each person's precomputed district membership, so results return quickly. Like other filters, it can be combined with additional filters (all conditions are additive) and [saved as a Saved Filter](filtering-people.md) for reuse — including for targeting [message campaigns](../texting/campaigns/).

{% hint style="info" %}
Only people with a geocoded address that resolved to a district will appear in a Legislative District filter. People without an address on file won't match.
{% endhint %}

### Viewing Legislators on a Person Profile

Open any person's profile and select the **Legislators** tab to see who currently represents them. For each office, Daisychain shows the legislator's name, party, district, and contact options (phone, website, social, and contact form), along with their district offices.

A few things you may see on this tab:

* **No address on file** — the person has no address, so no lookup can be performed.
* **No legislators found** — an address exists but didn't resolve to any districts.
* **Address precision** — when the address isn't a precise rooftop match, a tag indicates the precision level, and individual matches may show a likelihood percentage.
* **Vacant** — a seat with no current officeholder.

The tab updates automatically when a person's address changes and the new lookup completes.

### Inserting Legislator Info Into Messages and Charms

You can personalize text campaigns and [Charms](../texting/charms/) with a person's specific legislators using Liquid variables. The general path is:

```
person.representation.{country}.{legislature}.legislators[0].{field}
```

For example, to greet someone with their US House representative's name and office phone number:

```liquid
{% if person.representation.us.house.legislators[0] %}
Your representative is {{ person.representation.us.house.legislators[0].full_name }}.
Call {{ person.representation.us.house.legislators[0].phone }} and tell them to vote NO on HB 1234.
{% else %}
Find your representative: https://www.house.gov/representatives/find-your-representative
{% endif %}
```

Available fields include full name, party, district, office phone, website, contact-form URL, photo, social handles, and office addresses. The US Senate has two senators per state, referenced as `legislators[0]` and `legislators[1]`.

{% hint style="warning" %}
Always wrap legislator variables in `{% if %}` / `{% else %}` blocks. Legislative data depends on the person having an address on file, so a fallback ensures people without data still receive a useful message.
{% endhint %}

For the full list of variables, sample messages, and tips, see **[Inserting Legislative Info](../texting/personalized-content/inserting-legislative-info.md)**.

### Related

* [Inserting Legislative Info](../texting/personalized-content/inserting-legislative-info.md) — full Liquid variable reference and message examples.
* [Inserting Polling Place Info](../texting/personalized-content/inserting-polling-place-info.md) — voting location lookups via iwillvote.com.
* [Filters](filtering-people.md) — all available filter categories.
