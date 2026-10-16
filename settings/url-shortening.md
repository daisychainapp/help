---
description: >-
  In Daisychain, you can choose to automatically shorten URLs that you send in
  your texts. This allows you to track your link clicks and have a shorter
  overall message length.
icon: link
---

# URL Shortening

Head to **Settings > URL Shortening** to turn this feature on or off, and to select which domain you'd like to use for your URL. Our default link shorteners are:

* go.daisychain.app
* givelink.io
* eventlinks.org

We provide URL shortening for a few reasons:

* URL shortening enables Daisychain to track who clicked/tapped on the link you sent out.
* URL shortening enables you to keep your messages short, which can increase deliverability rates and reduce the number of segments[^1] in your messages.

{% hint style="warning" %}
Using a generic URL shortener (like bit.ly or TinyURL) makes it more likely that your messages gets flagged as spam and filtered out.
{% endhint %}

### Custom domains

You can use your own domain for shortened links. Custom short links can increase deliverability and brand recognition. Account admins can request one under **Settings > URL Shortening > Add a custom domain**:

1. Enter the domain you'd like to use and click **Request domain**. A subdomain like go.yourdomain.org works with any DNS provider. An apex domain like yourdomain.org works if your DNS provider supports CNAME flattening or ALIAS records, such as Cloudflare.
2. Add the two DNS records shown at your DNS provider. We check them automatically, and you can use **Verify** to re-check right away.
3. Once both records verify, our team approves the domain, usually within a business day, and emails you when it's ready. You can then select it as your **URL Shortening Domain**.

If your DNS is on Cloudflare, both records must be DNS-only (grey cloud). Keep both records in place permanently, since they are re-checked periodically.

Need help choosing a domain or setting up DNS? Email hello@daisychain.app and we can set it up on your behalf.

### URL Shortening FAQ

#### **Does Daisychain keep my link's Open Graph metadata when shortening URLs?**

Yes. You can find the Open Graph metadata we keep in our link shortening using tools like [OpenGraph.xyz](https://www.opengraph.xyz/) (paste a Daisychain shortened link to see what info we keep).

#### **Does Daisychain preserve URL parameters when shortening URLs?**

Yes. If you add URL parameters to a link, those parameters will be preserved when we shorten the URL. For instance if you link to abc.xyz?refcode=123, the refcode parameter will remain intact.

#### **How can I get previews for my links to appear?**

Not all links will appear as previews. Typically, a link must be the very first or last part of a message to generate a preview. Additionally, only one link preview per message will generate. You can test this out by sending yourself a preview message.

#### **Why aren't link previews working on recipients' devices?**

Each phone type and messaging software has its own way of handling link previews. For example, iPhones typically will only render a preview of any type when receiving an SMS if the contact is saved. Certain recipients will not receive the full preview regardless. Because of this, we recommend not relying on information in the link preview and including any vital content in your message text or in an image.

&#x20;

[^1]: 
