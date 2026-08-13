---
description: >-
  Quick Replies are templated messages that you can save, which makes things
  more efficient for messages you might want to reuse.
icon: file-lines
---

# Quick Replies

### Types of Quick Replies

#### 1. **Global Quick Replies**

* Always available to all texters in all campaigns.
* Great for messages you use often across multiple types of outreach efforts.&#x20;
* Can be customized for individual campaigns during campaign creation without affecting the global version.

#### 2. **Campaign-Specific Quick Replies**

* Can be added during Campaign Creation or added/edited after campaign launch via **Manage Replies > Settings > Quick Replies.**&#x43;reated directly during campaign creation (Step 2 – Content).
* Customized Campaign-Specific Quick Replies are only available in conversations with people who received that campaign.

### Organizing Quick Replies with Reply Sets

* Reply Sets are collections of Quick Replies grouped by a specific purpose or campaign type — like "Event Recruitment" or "Get Out the Vote."
* They make it easier to add multiple related Quick Replies to a campaign at once.
* You can create and manage Reply Sets in Settings → Channels → Texting → Quick Replies → Reply Sets.

### Creating and Managing Quick Replies

#### Add a Global Quick Reply

1. Go to Settings > Channels > Texting > Quick Replies&#x20;
2. Global tab and click Add.
3. Enter:
   * **Name:** for internal reference
   * **Keyboard Shortcut:** like `/vote` or `/rsvp`
   * **Body:** the message text — supports [variables](personalized-content/) like `{{ person.first_name }}` to personalize the messages.&#x20;
4. Optionally, assign Tags to help filter and organize replies. This is useful if you have LOTS of quick replies in your account.&#x20;
5. Optionally, add an [automation](#running-an-automation-when-a-quick-reply-is-sent) that runs whenever a texter sends this reply — for example, tagging the person to record what they said.
6. Click Save.

{% hint style="warning" %}
**Tags on a Quick Reply organize the reply, not the person.** They make replies easier to find in the inbox picker, and they are never applied to the people who receive the message. To tag a person when a reply is sent, use a [Quick Reply automation](#running-an-automation-when-a-quick-reply-is-sent) with an **Add a Tag** step.
{% endhint %}

#### Add a Campaign-Specific Quick Reply

1. In Step 2 – Content while creating a campaign, click Customize under Quick Replies.
2. Click Add Individual Reply.
3. In the pop-up window, you can add the the Name, Shortcut, Message Body, and optional Tags. The default name format `{Quick Reply Original Name} ({Campaign Name})` and will show at the top of the quick replies list in for texters managing conversations in the Inbox.&#x20;
4. Click Save. The reply will appear in a set below the standard Global Quick Replies, and will be available to texters only in that campaign.

#### Edit or Delete

* Click Edit to update text or shortcut.
* Click Delete to remove.
* Changes apply immediately wherever the Quick Reply is available.

***

### Using Quick Replies in Campaigns

#### While Creating a Campaign

1. When creating a [texting campaign](campaigns/), in the Content step, click Customize under Quick Replies.
2. Add entire Reply Sets, or create Campaign-Specific Replies.
3. Customize existing Global Quick Replies for this campaign only.

#### After a Campaign Launch

* Navigate to Manage Replies → Settings → Quick Replies for that campaign.
* Edit or add campaign-specific Quick Replies at any time while the campaign is active.

#### During Conversations

1. When messaging a contact, click the Quick Replies icon, which looks like a piece of paper in the bottom-left of the message box, like this: <i class="fa-file-lines">:file-lines:</i>
2. Search or filter by tags.
3. Click a reply to insert it into the message field.
4. Personalization tokens (e.g., `{{ person.first_name }}`) will auto-fill with each recipient's data.

***

### Running an Automation When a Quick Reply Is Sent

A Quick Reply can do more than send text. You can attach an [automation](../organizing/automations/) to it, and every time a texter sends that reply from the inbox, the automation runs on the person who received it.

This turns the inbox into a data-collection tool: the texter picks the reply that fits the conversation, and the record-keeping happens on its own.

#### What you can use it for

* **Record the answer as a tag.** A `/notinterested` reply tags the person "Not Interested." A `/rsvpyes` reply tags them "Event RSVP." Because the texter has to pick a reply anyway, your tags stay accurate without asking anyone to do a second step — and you can [filter and target](../managing-data/filtering-people.md) on those tags later.
* **Correct or reclassify a record.** A reply that tells someone their information has been fixed can tag them so the correction is visible on the person record and excludable from future sends.
* **Hand the conversation off.** A `/needsorganizer` reply assigns the person to a specific user or to a [Team](../settings/teams.md), so a real follow-up gets owned by someone.
* **Open a piece of work.** A reply about volunteering creates a card on a [Pathway](../organizing/pathways.md) in the right stage, so the ask shows up on a board instead of disappearing into a thread.
* **Follow up later, automatically.** Add a **Delay** step and then an email, so someone who asks for details in a text gets them the next morning without anyone remembering to send it.
* **Log event attendance.** With Mobilize connected, a reply confirming someone showed up can record the attendance status.

#### Setting it up

1. Go to **Settings > Channels > Texting > Quick Replies** and edit the reply (or create a new one).
2. Under **Run an automation when this Quick Reply is sent**, click **Add automation**.
3. Add your steps and click **Add Step** for each one, then **Save**.

Replies that have an automation attached are marked in the Quick Replies list, so you can see at a glance which ones do something.

The available steps are:

* **Add a Tag** — apply a tag to the person. Add multiple steps to apply multiple tags.
* **Assign Person to User** — assign to a specific user or a randomly selected member of a [Team](../settings/teams.md).
* **Create a Card** — add a card to a [Pathway](../organizing/pathways.md), with the stage and assignment you choose.
* **Delay** — pause for minutes, hours, or days, or until a specific day and time, before the next step.
* **Send an Email** — available once you have [configured email](../email/email-configuration.md).
* **Mobilize Attendance** — available if you've integrated [Mobilize](../integrations/mobilize.md).

There's no **Send a Message** step here: the Quick Reply is the message.

{% hint style="info" %}
Configuring Quick Reply automations requires an admin. Managers can edit the Quick Reply's name, shortcut, and message, and can see the automation's steps, but can't change them.
{% endhint %}

#### What texters see

When a texter selects a Quick Reply that has an automation, a lightning bolt appears next to the message box, highlighted to show the automation is armed. Clicking it shows exactly which steps will run.

If this particular conversation is the exception — the reply is right but the tag isn't — the texter can click **Skip for this message**. The automation is skipped for that one send only and stays armed for everyone else.

The automation runs after the message actually sends, and the run is recorded in the conversation thread, so you can see whether it ran, is still running (during a delay), or failed.

***

### Quick Reply Suggestions

If enabled in Settings, Daisychain can suggest the correct quick reply to use based on the context of incoming messages. The suggested Quick Reply will be auto-selected, and will pre-populate in the message composition box. Texters can choose to:

* Send the suggested Quick Reply
* Choose another Quick Reply
* Edit the message before sending, or write a message from scratch

Note that these are not AI-generated messages (like you might use in [Flows](flows.md)) — this option merely uses AI to help pre-select the right message.&#x20;

This feature is optional and off by default – you can toggle it on at any time by heading to _Settings > Channels > Texting > Quick Replies > Settings._&#x20;

***

### Best Practices

* **Use Shortcuts Wisely**: Pick easy-to-remember shortcuts like `/yes` or `/donorthanks`.
* **Leverage Tags**: Keep large reply libraries organized. Remember these tags organize the reply itself — to tag the person, [attach an automation](#running-an-automation-when-a-quick-reply-is-sent).
* **Let the Reply Do the Data Entry**: If you'd otherwise ask texters to tag people by hand, [attach an automation](#running-an-automation-when-a-quick-reply-is-sent) to the reply instead. Picking the right reply is something texters already do; tagging afterward is something they forget.
* **Personalize**: Use [variables](personalized-content/) to greet people by name or reference relevant details. Make sure to test before sending, to ensure personalization fields populate correctly.
* **Keep Replies Concise**: Short, clear replies are more likely to be read and understood.

By setting up well-organized Quick Replies and organizing them into Reply Sets, you can save time, keep messaging consistent, and ensure your team responds quickly to supporters.
