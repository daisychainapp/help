---
description: >-
  Automations are a powerful feature that can help make workflows more
  efficient.
icon: bolt
---

# Automations

Automations let you build powerful, multi-step workflows that run automatically when something happens — a donation comes in, someone RSVPs to an event, a new signup lands in your account. Instead of manually tagging, texting, and assigning people one by one, automations handle it for you.

**Here are a few examples of what you can do:**

* **Route new signups to organizers.** When someone signs up through EveryAction, tag them based on the signup page, assign them to the right team member, and kick off an introductory personalized text sequence with built-in delays.
* **Welcome new donors instantly.** When someone donates via ActBlue, automatically send them a personalized thank-you text, tag them as a donor, and assign them to an organizer for follow-up.
* **Onboard event RSVPs.** When someone RSVPs on Mobilize, send them a personalized confirmation text with event details, wait until the day before the event, then send a reminder message.
* **Escalate high-value actions.** When a donation over $100 comes in, create a card on a "High-Value Donors" pathway, assign the person to a senior donor organizer, and send a personal outreach text after a short delay.
* **Capture what a texting conversation revealed.** When a texter sends the "Not Interested" quick reply, tag the person so they can be excluded from the next send — see [Quick Reply automations](../../texting/quick-replies.md#running-an-automation-when-a-quick-reply-is-sent).

### Creating an Automation

Here's how to create an automation:

* Navigate to **Settings**, and then click on **Automations.**
* Click the **Add** button.
* Choose a **Trigger,** which is the event that will begin an automation. Triggers can be from tools you've integrated in your account (like a donation from [ActBlue](../../integrations/actblue.md) or an RSVP on [Mobilize](../../integrations/mobilize.md)), though some triggers (like "Stage Transition") are based purely on things happening within Daisychain.&#x20;

{% hint style="info" %}
**Some Notes on Triggers**

* The external triggers that are available on your account will depend on which tools have been setup as [**Integrations**](https://help.daisychain.app/integrations-overview) in your Daisychain account.
* You can select "Manually Triggered", which means you'll be able to manually trigger this automation on a per-person basis by clicking the small lightning icon in a Person's record.
* Automations run on all actions by default, but after you choose a trigger you can [add a filter](filtering-automations.md) to only run the automation when it matches certain specified conditions -- such as signups on specific pages, or donations over certain dollar amounts. Filtering your triggers requires using using the [JMESPath language.](https://jmespath.org/) Please reach out to support if you have questions about how to use this feature or need help writing JMESPath code to filter your triggers.​
{% endhint %}

* Once you've chosen a **Trigger,** select your first **Step** for your automation. Current Daisychain automation steps include:

{% hint style="info" %}
- **Add a Tag**, which lets you add a tag to a Person. (You can create multiple "Add a Tag" steps if you need to apply multiple tags).
- **Create a Card**, which lets you easily add a new Card to a [Pathway](../pathways.md) and set the Stage and Assignment.
- **Delay**, which is useful for pausing an automation (for minutes, hours, days -- or until a specific day or time) before proceeding to the next step.
- **Send a Message**, which makes it easy to send text messages which you have the option to personalize.
- **Assign Person to User,** which makes it easy to assign a Person to a User or randomly selected member of a given [Team](https://help.daisychain.app/teams).
- **Invite to Event,** which is only available for use if you've integrated Mobilize to your Daisychain account.
- **Mobilize Attendance**, which is only available for use if you've integrated Mobilize into your Daisychain account and reached out to the Mobilize team to activate this feature ([More info here](https://help.daisychain.app/mobilize))
- **Send an Email,** which is only available after you have [configured email.](../../email/email-configuration.md)
{% endhint %}

* You can add as many **Steps** as you'd like to an automation.
* You can also **Edit** an automation after you've created it if you need to modify, add, or remove steps.

### Automations That Live on a Quick Reply

Most automations live in **Settings > Automations** and are triggered by something arriving from outside — a donation, an RSVP, a signup. One kind is set up somewhere else: an automation attached to a [Quick Reply](../../texting/quick-replies.md#running-an-automation-when-a-quick-reply-is-sent), which runs when a texter sends that reply in the inbox.

Use it when the thing you want to record is *what the conversation revealed* — that someone is a yes, a no, a wrong number, or needs a call. The texter picks the reply they were going to pick anyway, and the tag, assignment, or card follows automatically. You set these up from **Settings > Channels > Texting > Quick Replies**, on the reply itself.

### Re-ordering Steps

If you need to change the order of steps in your automation, you can easily re-arrange them. Hover over any step to reveal the re-order icon (the up/down arrows). Click it to see **Move up** and **Move down** options, then select the direction you want to move the step. This makes it easy to insert a new step and then shuffle it into the right position, or rearrange an existing automation without having to delete and re-create steps.
