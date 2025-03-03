---
icon: chevrons-right
description: How to integrate Daisychain and Action Network
---

# Action Network

### **Overview**

With the Action Network <> Daisychain integration, when someone takes action on Action Network forms, petitions, events, and donations, that action can be represented in Daisychain and will be viewable in that person's timeline:\
‍

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

In Daisychain, you can use these actions as triggers for [Automations](../organizing/automations/). Note that this integration is only available to Action Network partners.

### **Setup**

1. **Get your Action Network API Key.** In your Action Network account, navigate to the "Details" menu, then select "API & Sync." Then, hit the "Generate API Key" button, and copy the resulting key to your clipboard -- it should be a long string of letters and numbers.\
   ​
2. **Add your Action Network API key to Daisychain.** In your Daisychain account, navigate to Settings > Integrations > Action Network (Add). Paste the API key you copied into the box, and hit "Save."\
   ​
3. **Copy the Web Hook URL.** After you hit save, you'll have access to a Web Hook URL. Copy that URL to your clipboard. You can always find this Web Hook URL at Settings > Integrations > Action Network (Manage).​\
   ​
4.  **Add your Web Hook to Action Network.** Head back to the "API & Sync" page in your Action Network account. From there, scroll down to the "Webhooks" section, and hit the "+ New Webhook" button. Paste in the webhook from your clipboard. Then, you'll want to select the "trigger" that imports people from Action Network into Daisychain:\
    ​

    <figure><img src="../.gitbook/assets/image.png" alt="" width="375"><figcaption></figcaption></figure>

You can [read more about these options in the Action Network documentation.](https://actionnetwork.org/docs/webhooks)[​](https://actionnetwork.org/docs/webhooks)

5. **Turn on the Webhook you just set up.** After this step, your Action Network integration will be live!

<figure><img src="../.gitbook/assets/image (23).png" alt="" width="375"><figcaption></figcaption></figure>

After your initial setup, people and data will be ingested from the Action Network to Daisychain based on the trigger you selected it. You can also [setup automations](../organizing/automations/) in Daisychain that are triggered when people sign up, donate, or RSVP in Action Network.

One note: if you unsubscribe someone from receiving SMS messages in Daisychain, that status should be updated in Action Network.
