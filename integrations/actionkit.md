---
description: How to integrate Daisychain and ActionKit
icon: plus
---

# ActionKit

### **Overview**

The ActionKit integration brings your ActionKit users into Daisychain as people and keeps them up to date. It also sends each action people take on your ActionKit pages to Daisychain as it happens, so you can see it on the person's timeline and use it to trigger [Automations](../organizing/automations/).

The integration does two things:

* **People sync.** The first import brings in all of your ActionKit users. After that, Daisychain checks ActionKit every hour for new and updated users.
* **Actions.** Petition signatures, signups, donations, event signups and other actions are sent to Daisychain in real time, starting from the moment you connect.

### **Setup**

1. **Create a staff user for Daisychain in ActionKit.** We recommend a dedicated staff user rather than a personal login. It needs REST API access to read users and phones, and to manage Push API endpoints.
2. **Add the integration in Daisychain.** Go to Settings > Integrations > ActionKit (Add) and enter:
   * **Hostname**: the address of your ActionKit instance, such as `act.example.org`.
   * **Username** and **Password**: the staff user's login.
3. **Decide whether to subscribe imported people to text messages.** This is off by default. Read [Text message subscriptions](actionkit.md#text-message-subscriptions) below before you turn it on.
4. **Click "Save."** Daisychain checks the login, then starts the first import.

The first import can take a while for a large list. You can leave the page and the import keeps running. To check on it, go to Settings > Integrations > ActionKit (Manage), where you'll also see when the last sync ran and how many people have been imported.

You don't need to set anything up in ActionKit for actions. Daisychain creates a Push API endpoint named "Daisychain" in your ActionKit instance for you. Please don't edit or remove it, since that is how actions reach Daisychain.

### **What gets imported**

For each ActionKit user, Daisychain imports:

* First and last name
* Email address
* Phone numbers. If the user has a mobile number, it becomes their primary phone.
* Mailing address
* Their ActionKit user ID, saved as an identifier on the person, which is how Daisychain matches them on later syncs

The import covers all of the users in your ActionKit instance. It can't be limited to a list, page or mailing. ActionKit custom user fields are not imported.

After the first import, the hourly sync picks up new users and changes to existing ones. You can also start a sync yourself with the "Sync Now" button on the integration's page.

### **Email subscriptions**

People who are subscribed to email in ActionKit are subscribed to email in Daisychain. If someone has already unsubscribed from your email in Daisychain, they stay unsubscribed.

Unsubscribes made in ActionKit are not synced to Daisychain.

### **Text message subscriptions**

ActionKit has no built-in way to record whether someone agreed to receive texts, so Daisychain can't tell which of your users opted in. By default, imported people are not subscribed to text messages.

If your organization collected these mobile numbers with consent to text them, you can turn on "Subscribe imported people to text messages." When it's on:

* The first import subscribes every ActionKit user with a mobile number, which can be your whole list. Each hourly sync subscribes new and updated users.
* Only numbers ActionKit lists as mobile are subscribed.
* Anyone who has already opted out in Daisychain, or whose number is on your opt-out list, stays opted out.

{% hint style="warning" %}
ActionKit doesn't record SMS opt-outs. If people opted out of your texts in another texting tool, turning this on will subscribe them again unless Daisychain already knows about the opt-out. Make sure those opt-outs are in Daisychain before you turn it on.
{% endhint %}

You can change this setting later at Settings > Integrations > ActionKit (Manage).

### **Actions**

When someone takes action on an ActionKit page, the action appears on their timeline in Daisychain within moments. If the person isn't in Daisychain yet, they're added.

A few things to know:

* Actions are sent from the time you connect the integration onward. Actions taken before that are not imported.
* Actions on Import pages (CSV uploads into ActionKit) and unsubscribes are not sent.

The integration's page shows whether ActionKit is sending actions and when the last one was received.

### **Triggering automations**

Choose the ActionKit "Action taken" trigger to run an [Automation](../organizing/automations/) whenever someone takes an action on one of your ActionKit pages. From there you can send a text, add a tag, create a card on a [Pathway](../organizing/pathways.md), or use any other automation step.

By default the automation runs on every action. To narrow it, [add a filter](../organizing/automations/filtering-automations.md). You can describe what you want in plain English, for example:

* "Petition signatures"
* "Actions on the save-the-park page"
* "Event signups from new users"

### **Filtering people by ActionKit page**

On the People page, the "ActionKit Page" [filter](../managing-data/filtering-people.md) finds people who took action on one or more ActionKit pages, or who did not. It only includes actions ActionKit has sent since the integration was connected.

### **If the integration is disabled**

If ActionKit rejects the staff user's login, for example after a password change, Daisychain disables the integration and shows a notice on its page. Enter the staff user's current password there to turn it back on.

### **Removing the integration**

Removing the integration stops the sync and stops ActionKit from sending actions. People who were already imported stay in Daisychain.

### **Frequently Asked Questions**

<details>

<summary>Does Daisychain write anything back to ActionKit?</summary>

No. Daisychain reads users and receives actions from ActionKit. It doesn't change your ActionKit users or record anything on them. The only thing it creates in ActionKit is the "Daisychain" Push API endpoint.

</details>

<details>

<summary>Can I import only some of my ActionKit users?</summary>

Not at this time. The import brings in every user. Once they're in Daisychain you can use [filters](../managing-data/filtering-people.md) and [tags](../managing-data/tags.md) to work with the group you need.

</details>
