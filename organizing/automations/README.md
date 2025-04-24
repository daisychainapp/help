---
description: >-
  Automations are a powerful feature that can help make workflows more
  efficient.
icon: bolt
---

# Automations

Here's how to create an automation:

* Navigate to **Settings**, and then click on **Automations.**
* Click the **Add** button.
* Choose a **Trigger,** which is the event that will begin an automation.

{% hint style="info" %}
**Some Notes on Triggers**

* The triggers that are available on your account will depend on which external tools have been setup as [**Integrations**](https://help.daisychain.app/integrations-overview) in your Daisychain account.
* You can select "Manually Triggered", which means you'll be able to manually trigger this automation on a per-person basis by clicking the small lightning icon in a Person's record.\\
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
