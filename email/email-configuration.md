---
description: How to set up email senders and layouts.
icon: envelope-circle-check
---

# Email Configuration

To start sending email in Daisychain, you'll need to have do a bit of setup.&#x20;

#### Senders

Navigate to _Settings > Channels > Email > Senders > Add_ to begin the three step configuration wizard which will walk you through the following three steps:

1. Setup your identity by entering your display name and email address
2. Verify your domain by adding three CNAME records to your DNS provider. _If you're not sure what that means, ask your website administrator or IT department._&#x20;
3. Confirmation and completion!&#x20;

{% hint style="success" %}
If you've already configured your domain in Daisychain and are just adding a new sender/name, you'll be able to automatically skip Step 2. &#x20;
{% endhint %}

#### Layouts

A layout is the reusable "frame" that wraps the content of every email you send — the header, footer, fonts, colors, and spacing. The content you write for each individual email is dropped into the layout when the email is sent.

Your Daisychain account comes with a default **Basic** layout. It's simple and readable for recipients on a wide variety of email clients and devices, and it includes the things that are legally required for automated email:

* Account Name
* Mailing Address
* Unsubscribe Link

You can find your layouts under _Settings > Channels > Email > Layouts_.

#### Editing a layout

Open a layout to edit it. You'll see two tabs:

* **Templates** — where you edit the layout itself. There are two editors:
  * **MJML Markup** — the structure and content of the layout.
  * **CSS** — styling that applies across the layout.
* **Preview** — a live rendering of the email so you can check your changes before saving.

Layouts are written in [MJML](https://mjml.io/documentation/), a markup language designed specifically for email. MJML uses its own tags — like `<mj-section>`, `<mj-column>`, and `<mj-text>` — which are automatically converted into the kind of HTML that displays reliably across email clients. When you're done, switch to the **Preview** tab to confirm it looks right, then hit **Save**.

{% hint style="info" %}
The built-in **Basic** layout can't be edited in place. The first time you save changes to it, you'll see **Save as New Template** — this creates your own editable copy and leaves the original untouched. After that, you'll have a normal **Save** button for future edits. Be sure your campaigns and automations are set to use your new layout.
{% endhint %}

{% hint style="warning" %}
Because layouts are MJML, you can't simply paste raw HTML anywhere in the editor — HTML placed on its own will be dropped when the email is built. To include HTML, put it **inside** an MJML tag:

* Use `<mj-text>` for text and inline formatting (links, line breaks, bold, colored spans). This is the right choice for most content, including disclaimers.
* Use `<mj-raw>` when you need to pass a block of custom HTML through untouched.
{% endhint %}

#### Editing the footer or disclaimer

The footer lives near the bottom of the layout's MJML, in the `<mj-text>` block that contains the unsubscribe link and your mailing address. To add a compliance line such as a "Paid for by" disclaimer, add a text block in that area, for example:

```html
<mj-text align="center" font-size="12px" color="#888">
  Paid for by Perry 2026, Stacey Dolan Treasurer. Approved by Jack Perry.
</mj-text>
```

#### Dynamic content with Liquid

Layouts can include [Liquid](https://shopify.github.io/liquid/) tags that are filled in for each recipient when the email is sent. The default layout uses a few of these:

* `{{ account.name }}` — your account/organization name
* `{{ account.customer_address }}` — your mailing address
* `{% unsubscribe_url %}` — the recipient's one-click unsubscribe link

{% hint style="info" %}
Your legal name and mailing address come from your account details and aren't edited in the layout itself. To change them, contact support and we'll update them for you — every layout that uses `{{ account.customer_address }}` will pick up the change automatically.
{% endhint %}
