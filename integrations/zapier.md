---
description: How to use Zapier to integrate with thousands of apps
icon: asterisk
---

# Zapier

Zapier is a powerful tool that you can use to link up Daisychain with thousands of other applications, including common tools like Google Forms, EventBright, Facebook Lead Ads, Slack, and more.

Here's the basics of setting up Zapier with Daisychain:

1. If you don't already have a Zapier account, you can [sign up for one here.](https://zapier.com/sign-up)\
   ​
2. [Click here](https://zapier.com/developer/public-invite/171650/1e0a3738d737b92624878904529a3d2a/) to accept the invitation to use Daisychain with Zapier.\
   ​
3. In Zapier, click the "Create a Zap" button.\
   ​
4. Then, Zapier will walk you through the setup process. This will include:<br>
   1. **Selecting a Trigger.** This could be something like a Google Form submission.<br>
   2. **Setting up your Action.** This will be where you search for and select Daisychain from the list of available apps. To connect Zapier to Daisychain, you'll need an API key, which you can get by Navigating to Daisychain Settings > API Keys, and generating a key that you can paste into the authentication box in Zapier.

A few notes about using Zapier with Daisychain:

* Be careful when mapping your fields, and make sure to run tests to ensure the data is flowing into Daisychain the way you want it to.\
  ​
* When a new person is imported via Zapier, you can use that as a trigger for Automations _within_ Daisychain. Just head to the Automations section and select "Record Person Action" as a trigger.\
  ​
*   When setting up your "Zap", you'll need to select the "Action" that is performed when the Zap runs, and you'll have two options:​<br>

    1\) "Record Person Action"<br>

    2\) "Create Person Tag"\
    ​\
    If you want, you can configure your Zap to first record the person, and then add a tag to that person as a subsequent Action step.

{% hint style="info" %}
Using Zapier can be tricky, so don't hesitate to reach out to our team if you need any help!
{% endhint %}

### Using Zapier with Automations

When someone is imported into Daisychain via a Zap, you can automatically trigger an Automation to take action — like sending a welcome text, adding a tag, creating a card on a Pathway, or assigning someone to an organizer.

Here's how to set it up:

1. Go to **Settings > Automations** and click **Add**.
2. Select **Record Person Action** as the trigger.
3. Add your automation steps (send a message, add a tag, create a card, etc.).

By default, the automation will fire for _all_ Record Person Action triggers — not just those from Zapier. If you have multiple integrations using this trigger, you'll want to add a filter so the automation only runs for your specific Zap.

#### Filtering by Zap ID

To limit the automation to a specific Zap, click the **Filter Automation** option after selecting your trigger, and add the following JMESPath expression:

```
action.zap.id == '123456789'
```

Replace `123456789` with your actual Zap ID, which you can find in the URL when editing your Zap in Zapier.

If you'd like the automation to fire for multiple Zaps, you can use the `||` (or) operator:

```
action.zap.id == '123456789' || action.zap.id == '987654321'
```
