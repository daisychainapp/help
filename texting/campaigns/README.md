---
description: In Daisychain, it's simple to create powerful text message campaigns.
icon: bullhorn
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: false
---

# Campaigns

{% embed url="https://www.loom.com/share/028d65993a014c76914fd6103f77c587?sid=32f075c3-d624-426e-a498-bb30ddc989c3" %}



Campaigns are Daisychain's feature that lets you quickly send messages to as many people as you'd like. This is the most powerful way to send a message to multiple people, since it enables features not found elsewhere in Daisychain, including:

* Scheduling
* Advanced analytics
* Message validation and suggestions
* Optimized outreach for [integrated tools (like ActBlue and Mobilize)](/broken/pages/llwdLYezFIRWokIsPIWu)
* Access to the [Reply Queue](managing-replies.md)
* Advanced targeting using Includes and Excludes

To create a campaign, navigate to the Campaigns section of Daisychain and click "New Campaign" to create an entirely new campaign, or click "Clone" to duplicate an existing campaign.&#x20;

### Step One: Basics

Here is where you'll set up the basic parameters of your campaign. You'll add the following fields:

* **Campaign Name:** You'll be able to search by this later.
* **Audience:** Your audience is who you are sending this campaign to. You can either send to your full list or send to a specific subset using [uploads](../../managing-data/csv-imports.md), [saved filters](../../managing-data/filtering-people.md), or lists from external tools.&#x20;

{% hint style="success" %}
**Advanced Audience Building**

If you choose more than one list or saved filter when building an audience, they’re combined with an OR.&#x20;

If a person is on a list or saved filter selected in the "Don't send to" menu, they won’t get the campaign—even if they were part of a list or saved filter selected in the "Send to" menu.\
\
In the example below, the campaign will be sent to people who are are either in the "Donors and Volunteers" saved filter OR the "CSV Import Test" list, but it will exclude anyone on the "Sample List" imported from EveryAction or the "500 Blue Wall" list. &#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>

**Goal:** Adding a goal will impact what is tracked in your Campaign Report/Analytics and enable smart links that can pre-fill the forms on landing pages. The default goal is to send a basic message, but other goals will be available if you have the [ActBlue](../../integrations/actblue.md) or [Mobilize](../../integrations/mobilize.md) integrations activated.&#x20;

### Step Two: Content

In this step,  is where you will add what is actually sent in your campaign. Add compelling content that will engage your recipients.

<figure><img src="../../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>

**Message Preview**\
You can use the message preview tool to cycle between recipients to see what your messages look like and ensure [personalized content](../personalized-content/) is showing up as expected.&#x20;

**Content Assistant**\
The "Content Assistant" will display basic information about your messages (such as the SMS segment count) and will flag any possible spam words.&#x20;

**Deliverability Best Practices**\
In the "Deliverability Best Practices" section, you'll see checkboxes that will turn green when you include opt-out language and introduce yourself using organization name (your Daisychain account name). Following these best practices will help maximize the delivery of your messages.&#x20;

**Send Test Messages**\
Click "send a test message" link at the bottom of the message preview to send a text message here to yourself or other members of your team. Note that these test messages will send the content displayed for person currently selected in the "preview message."&#x20;

![](https://44727351.fs1.hubspotusercontent-na1.net/hubfs/44727351/Screenshot%202024-03-14%20at%201-15-53%E2%80%AFPM-png.png)

**Scheduling:** Your campaign may be sent immediately, or scheduled to be sent at a later date or time. Note that targeting is re-calculated at the time when the campaign is actually sent.&#x20;

{% hint style="info" %}
Daisychain checks for scheduled campaigns every 10 minutes. For example, if you schedule a campaign to be sent at 1:03pm, sending won't actually begin until 1:10pm.
{% endhint %}

**Setup A/B Testing:** When creating your campaign, you can [setup A/B testing](a-b-testing.md) to easily create experiments.

### Step 3: Review

During this step, you can review the number of recipients who will receive your message.&#x20;

### Step 4: Report

Once your campaign is sent, you will be taken to the [Campaign Report](campaign-report.md) page. This is a page of analytics for your campaign that contains stats including:

* Audience Size
* Number of messages delivered
* Number of replies received
* Number of opt-outs
* Number of clicks (if you have [short-links](../../settings/url-shortening.md) turned on)
* Number of conversions (if you are using an integrated tool and a campaign goal)

On this step, there are also links to:

* Download all messages sent in the campaign
* View information about which people clicked a link
* Manage the "[reply queue](managing-replies.md)"
* See details of any messages that weren't delivered
