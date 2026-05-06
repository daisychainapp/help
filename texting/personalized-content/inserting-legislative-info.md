---
description: How to insert legislative information into your Daisychain messages.
icon: landmark-dome
---

# Inserting Legislative Info

{% hint style="info" %}
Legislative data is powered by the and is based on each person's address. For the lookup to work, **the person must have an address on file in Daisychain** — at minimum a ZIP code, though a full street address produces the most accurate results.&#x20;
{% endhint %}

#### Overview

Daisychain can automatically look up a person's elected officials — including their US House representative and US Senators — and insert that information directly into your messages using variables.

This is especially useful for advocacy campaigns where you want to tell supporters who their representative is, provide a phone number to call, or link to a contact form.

#### How It Works

Legislative data lives under `person.representation`, organized by country and legislature. The general path is:

```
person.representation.{country}.{legislature}.legislators[0].{field}
```

For US federal legislatures, the available legislature keys are:

| Legislature Key | What It Refers To           |
| --------------- | --------------------------- |
| `house`         | US House of Representatives |
| `senate`        | US Senate                   |

Each legislature also includes an `area` object with the matched district info, and a `legislators` array with the elected officials for that district.

#### Commonly Used Variables

Here are the variables you'll use most often:

| Variable                                                               | Description                                       |
| ---------------------------------------------------------------------- | ------------------------------------------------- |
| `{{ person.representation.us.house.legislators[0].full_name }}`        | Full name of the person's US House representative |
| `{{ person.representation.us.house.legislators[0].party }}`            | Party affiliation                                 |
| `{{ person.representation.us.house.legislators[0].phone }}`            | Office phone number                               |
| `{{ person.representation.us.house.legislators[0].contact_form_url }}` | Link to the representative's contact form         |
| `{{ person.representation.us.house.legislators[0].district }}`         | District name                                     |
| `{{ person.representation.us.house.area.name }}`                       | Name of the matched district area                 |
| `{{ person.representation.us.senate.legislators[0].full_name }}`       | Full name of the person's first US Senator        |
| `{{ person.representation.us.senate.legislators[1].full_name }}`       | Full name of the person's second US Senator       |

{% hint style="warning" %}
**US Senate has two legislators per state.** Use `legislators[0]` and `legislators[1]` to reference each senator. House districts typically have one representative, so `legislators[0]` is usually all you need.
{% endhint %}

#### Sample Messages

**Calling a US House Representative**

```liquid
Hey {{ person.first_name | default: "friend" }}, we need your help to stop HB 1234!

{% if person.representation.us.house.legislators[0] %}
Your representative is {{ person.representation.us.house.legislators[0].full_name }}. Call their office at {{ person.representation.us.house.legislators[0].phone }} and tell them to vote NO on HB 1234.
{% else %}
Look up your representative and call their office to tell them to vote NO on HB 1234: https://www.house.gov/representatives/find-your-representative
{% endif %}
```

**Contacting a Senator via Web Form**

```liquid
Hi {{ person.first_name | default: "there" }}, the Senate is about to vote on the Clean Air Act. Can you take 2 minutes to tell your senators to vote YES?

{% if person.representation.us.senate.legislators[0] %}
Contact {{ person.representation.us.senate.legislators[0].full_name }}: {{ person.representation.us.senate.legislators[0].contact_form_url }}
{% endif %}
{% if person.representation.us.senate.legislators[1] %}
Contact {{ person.representation.us.senate.legislators[1].full_name }}: {{ person.representation.us.senate.legislators[1].contact_form_url }}
{% endif %}
{% unless person.representation.us.senate.legislators[0] %}
Find your senators here: https://www.senate.gov/senators/senators-contact.htm
{% endunless %}{% endcode %}
```

#### District and Area Info

You can also reference the district or area that was matched for a given person:

<table><thead><tr><th width="498.90234375">Variable</th><th>Description</th></tr></thead><tbody><tr><td><code>{{ person.representation.us.house.area.name }}</code></td><td>District name (e.g., "New York's 10th Congressional District")</td></tr><tr><td><code>{{ person.representation.us.house.area.abbreviation }}</code></td><td>Short form (e.g., "NY-10")</td></tr></tbody></table>

#### Office Info

Each legislator has an `offices` array and a `closest_office` shortcut (the nearest known office based on the person's address):

<table><thead><tr><th width="458.0078125">Variable</th><th>Description</th></tr></thead><tbody><tr><td><code>{{ person.representation.us.house.legislators[0].closest_office.full_address }}</code></td><td>Full address of the nearest office</td></tr><tr><td><code>{{ person.representation.us.house.legislators[0].closest_office.phone }}</code></td><td>Phone number for the nearest office</td></tr><tr><td><code>{{ person.representation.us.house.legislators[0].closest_office.name }}</code></td><td>Office name (e.g., "District Office")</td></tr><tr><td><code>{{ person.representation.us.house.legislators[0].offices[0].full_address }}</code></td><td>Address of the first listed office</td></tr></tbody></table>

#### Full List of Legislator Fields

<table><thead><tr><th width="163.0859375">Field</th><th>Variable (example using US House)</th></tr></thead><tbody><tr><td>Full Name</td><td><code>{{ person.representation.us.house.legislators[0].full_name }}</code></td></tr><tr><td>First Name</td><td><code>{{ person.representation.us.house.legislators[0].first_name }}</code></td></tr><tr><td>Last Name</td><td><code>{{ person.representation.us.house.legislators[0].last_name }}</code></td></tr><tr><td>Party</td><td><code>{{ person.representation.us.house.legislators[0].party }}</code></td></tr><tr><td>Position</td><td><code>{{ person.representation.us.house.legislators[0].position_name }}</code></td></tr><tr><td>District</td><td><code>{{ person.representation.us.house.legislators[0].district }}</code></td></tr><tr><td>District Abbreviation</td><td><code>{{ person.representation.us.house.legislators[0].district_abbreviation }}</code></td></tr><tr><td>Legislature</td><td><code>{{ person.representation.us.house.legislators[0].legislature }}</code></td></tr><tr><td>Phone</td><td><code>{{ person.representation.us.house.legislators[0].phone }}</code></td></tr><tr><td>Website</td><td><code>{{ person.representation.us.house.legislators[0].url }}</code></td></tr><tr><td>Contact Form</td><td><code>{{ person.representation.us.house.legislators[0].contact_form_url }}</code></td></tr><tr><td>Photo URL</td><td><code>{{ person.representation.us.house.legislators[0].photo_url }}</code></td></tr><tr><td>Twitter</td><td><code>{{ person.representation.us.house.legislators[0].twitter }}</code></td></tr><tr><td>Twitter URL</td><td><code>{{ person.representation.us.house.legislators[0].twitter_url }}</code></td></tr><tr><td>Facebook</td><td><code>{{ person.representation.us.house.legislators[0].facebook }}</code></td></tr><tr><td>Facebook URL</td><td><code>{{ person.representation.us.house.legislators[0].facebook_url }}</code></td></tr></tbody></table>

#### Tips

* **Always use fallback messages.** Legislative data depends on the person having an address on file. Wrap your legislator variables in `{% if %}` / `{% else %}` blocks so people without data still get a useful message with a link to look up their rep manually.
* **Swap out the legislature key** to target different bodies. Replace `house` with `senate` , for example.
* **Senate has two entries.** Remember to use both `legislators[0]` and `legislators[1]` when messaging about US Senators or when both senators are relevant to your ask.
* **Always send test messages** to ensure variables are working as expected.&#x20;

