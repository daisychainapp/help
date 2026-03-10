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
5. Click Save.

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
* **Leverage Tags**: Keep large reply libraries organized.
* **Personalize**: Use [variables](personalized-content/) to greet people by name or reference relevant details. Make sure to test before sending, to ensure personalization fields populate correctly.
* **Keep Replies Concise**: Short, clear replies are more likely to be read and understood.

By setting up well-organized Quick Replies and organizing them into Reply Sets, you can save time, keep messaging consistent, and ensure your team responds quickly to supporters.
