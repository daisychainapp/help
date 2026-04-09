---
description: Flows let you automate multi-step conversations with supporters.
icon: code-branch
---

# Flows

{% hint style="success" %}
**Want help getting started with your first Flow?** We'd love to talk. Just [book a training](https://daisychain.app/training) with our team. Flows are included with any [Daisychain subscription.](https://www.daisychain.app/pricing)
{% endhint %}

## What is a Flow?

A **Flow** is a conversation that can be triggered when a supporter replies to a message sent through [campaigns](campaigns/ "mention") or [automations](../organizing/automations/ "mention"), or when they text into using one of your [keywords.md](keywords.md "mention").&#x20;

Unlike traditional peer-to-peer texting, supporters get instant responses instead of waiting for the next available volunteer, and replies can be hyper-personalized rather than pulled from a set of static templates.

Flows can be AI-powered, use specific templated messages that you write, or combine both approaches. They can answer questions, ask follow-up questions, look up legislators, find polling places, collect personal stories and data, schedule reminders, nudge people who go quiet, and escalate to a bigger ask — all without manual intervention.

Flows can:

* Use AI to generate personalized replies OR use specific templated messages that you write
* Ask follow-up questions
* Respond with personalized messages
* Look up legislator info
* Schedule messages for later
* Nudge non-responsive people to reply
* Update data fields

## Creating a New Flow

1. **Go to the Flows tab**\
   From your campaign dashboard, click the Flows icon in the left-hand sidebar.
2. **Click "New Flow"**\
   Give your Flow a name. You can always rename it later.
3. **Add your first Node**\
   A Flow starts when a supporter replies to your broadcast message. Click the green **+** button to add a Node.

## Node Types

When adding a Node, you’ll choose one of three types:

### Intelligence Node (AI-powered)

Let the AI interpret the supporter’s message and respond using your custom instructions.

* You can choose AI models from Open AI and Anthropic.
* You can toggle whether the AI should send a reply message or just analyze silently. (For now, this toggle is always on.)
* The AI will have access to all [standard-fields.md](../managing-data/standard-fields.md "mention") and [custom-fields.md](../managing-data/custom-fields.md "mention") associated with a given person, and will use the data stored in those fields to inform the conversation.&#x20;
* Currently, the AI does not have access to [notes.md](../organizing/notes.md "mention") associated with that Person or actions from the Person's timeline.&#x20;
* Your custom instructions should provide clarity on the role of the AI, how it should respond, what capabilities it does (or doesn't) have, and any guardrails. Example below.&#x20;

{% hint style="success" %}
**Best Practices For Using Intelligence Nodes**

* Keep instructions clear — AI performs better with direct guidance
* Always disclose that an AI, chatbot, or "virtual organizer" is generating messages
* [Test your Flow](flows.md#testing-your-flow) in the the Simulator before going live
{% endhint %}

{% hint style="info" %}
**Example Instructions for an Intelligence Node**

You are a community organizer helping supporters decide whether to attend an upcoming event.

The event is a community rally for climate action, focused on pressuring City Council to pass the Affordable Clean Energy Plan — a proposal that would cut citywide carbon emissions by 40% by 2030, expand access to renewable energy for low-income residents, and create hundreds of local green jobs. It takes place on Saturday, October 12th at 3 PM at Springfield Park. There will be speakers, music, and snacks. The vibe is family-friendly and welcoming to newcomers.

Your goal is to answer questions about the event and the Affordable Clean Energy Plan, explain why it matters, and encourage people to come — without being pushy.

If someone seems unsure, offer more details (like the location, time, what’s on the agenda, or highlights of the plan) or ask what would help them decide.

Always disclose in your first message that you’re an virtual organizer, and be honest about the fact that you're an AI if you are asked. &#x20;

If you don't know the answer to a question, disclose that you don't know. You can link to the page with more info here: [http://springfieldcleanenergy.com/](http://springfieldcleanenergy.com/)&#x20;
{% endhint %}

#### AI Agent Guidelines

AI Agent Guidelines let you control the personality, tone, and style of AI-generated messages across your Flows. Guidelines are applied at two levels: **account-level** (default for all Flows) and **flow-level** (custom overrides for individual Flows).

**Account-Level Guidelines**

Account-level guidelines apply to every Flow in your account by default. This is the best place to define your organization's general voice and tone so you don't have to repeat yourself in every Flow.

To configure account-level guidelines, go to **Settings > Account > Flows**. You'll see the current guidelines displayed under "AI Agent Guidelines." Click **Edit** to customize them.

By default, Daisychain includes a set of system guidelines focused on SMS best practices — things like keeping messages short, using plain text, and not inventing URLs. You can customize these to reflect your organization's brand voice, communication style, or any universal rules you want the AI to follow.

**Flow-Level Guidelines**

Individual Flows can override the account-level guidelines with their own custom settings. This is useful when a specific Flow needs a different tone or personality — for example, a fundraising Flow might be more direct, while a volunteer recruitment Flow might be warmer and more conversational.

To set flow-level guidelines, open your Flow and click **Flow Settings** in the right sidebar. Under "AI Agent Guidelines," click **Edit Guidelines**. You'll see the inherited account-level guidelines pre-populated. Edit the text to create flow-specific guidelines, then click **Save Guidelines**.

If a Flow has custom guidelines, those will be used _instead of_ the account-level defaults. If no custom guidelines are set, the Flow inherits the account-level guidelines automatically.

#### What to Include in Your Guidelines

Guidelines are inserted directly into the AI's prompt, so write them as clear instructions. Some things you might include:

* **Tone and voice:** e.g., "Be friendly and casual" or "Use a professional, respectful tone"
* **Message length:** e.g., "Keep messages to 1–2 sentences"
* **Emoji and formatting rules:** e.g., "No emojis" or "Use emojis sparingly"
* **Language preferences:** e.g., "Respond in Spanish if the supporter writes in Spanish"
* **Guardrails:** e.g., "Never discuss topics outside of the upcoming election" or "Always disclose that you are an AI"

These guidelines work alongside the custom instructions you write in each Intelligence Node. Think of it this way: guidelines define _how_ the AI communicates (style and personality), while node instructions define _what_ the AI is communicating about (context, goals, and content).

#### Node Transitions

Transitions let your Flow decide what node to proceed to next based on how someone replies.

Transitions only work with Intelligence Nodes. If you're using an Intelligence Node, you can add one or more Transitions.&#x20;

1. Click the "Add Transition" Button
2. Give it a short name (like “Wants to attend the event”)
3. Describe the condition and provide a few examples of what the reply should sound like, and provide "true" and "false" instructions at the end. (Example below)

{% hint style="info" %}
**Example Transition Instructions**

The user is making a commitment to take an action. This includes messages like:

* 'I will go to the rally'
* 'I'll be there and will ask my friends to join'
* Any variations where the user is committing to attend

Return "true" if the message is making an explicit commitment to attend the rally, "false" if they are not.
{% endhint %}

The AI will check each transition in order and follow the first one that matches. Here's an example:

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Transitions must be connected to another node in order to function correctly.&#x20;
{% endhint %}

### Send a Message Node

This node type allows you to send a quick response back to the supporter — with no logic and no AI. Currently, the send message node will only send a single message. Think of it like an "autoresponder", since a "Send a Message" node will always send the same outgoing message, regardless of the content of the incoming message.&#x20;

### Automation Steps Node

Perform actions like applying [tags.md](../managing-data/tags.md "mention"), adding people to [pathways.md](../organizing/pathways.md "mention"), making [assignments.md](../organizing/assignments.md "mention"), sending [emails](../email/email-overview.md), and more.

## Tools and Settings for Intelligence Nodes

Tools and Procedures can extend what an Intelligence Node can do inside a Flow. They allow the Flow to take specific actions rather than just sending a message. For example, a tool might look up data, create a tag, or schedule a follow-up.

Each Intelligence Node can be configured with one or more tools, depending on what you want the Flow to accomplish. To add a tool to your Intelligence Node, type `@` in the Instructions box and select from the available tools. You can also click the "+ Add Tool" button. Added tools appear as chips below the Instructions field, and you can click "Edit" on any tool to configure it further.

Referencing tools by name in your Instructions (e.g., "use the @Collect Custom Field tool to record their answer") helps the Flow understand when and how to use them.

### **Legislative Lookup Tool**

The Legislative Lookup tool lets your Flow automatically identify federal elected officials in the US based on a person's location. This is especially useful in advocacy campaigns so you can help a person look up their local representative without sending them to a separate lookup tool.&#x20;

When using this tool, you'll want to provide  instructions that specify what information is needed to look up their elected official.

{% hint style="info" %}
**Sample Instructions for an Intelligence Node using the Legislative Lookup tool**

You are a community organizer helping supporters take action to stop House Bill 123, a proposed federal law that would restrict clean energy access and reduce funding for solar power. Your goal is to help people understand why the bill matters, identify their elected officials using the <mark style="color:$primary;">**@Legislative Lookup tool**</mark>, and encourage them to contact those officials.

As for their ZIP code first to look up their representative in the US House of Representatives. If their ZIP code isn't enough to determine who their representative is, explain the situation to the supporter and ask for their full address.&#x20;

Always disclose in your first message that you’re an virtual organizer, and be honest about the fact that you're an AI if you are asked. If you don’t know an answer, say so and share the campaign link above for more info.
{% endhint %}

### **Scheduler Tool**&#x20;

The Scheduler Tool lets the Flow automatically schedule a follow-up SMS message at a specific date and time. This is especially useful when you want to check back in about a commitment someone made or an action they are planning to take (like attending a meeting or showing up to an event) without requiring manual follow-up.

When using this tool, you’ll want to guide the person to share when they’re planning to take the action. Once they give a date or time, the Scheduler Tool can trigger a reminder message at that exact moment. For best results with teh schedule tool, include a section of your Instructions that invokes it by name ("scheduler tool") and be specific about how you want it to behave.&#x20;

{% hint style="info" %}
**Sample Instructions for an Intelligence Node using the Scheduler tool**

You are virtual organizing assistant helping the contact make a plan to visit their congressional office. Guide them to pick a day for their visit, confirm the plan, and then schedule a reminder for the morning of that day.

Ask one question at a time. Accept any reply that clearly indicates intention or timing. If their answer is unclear, ask one brief clarifying question.&#x20;

Once they give a usable date, use the <mark style="color:$primary;">**@Scheduler Tool**</mark> to set a follow-up message for the morning of that date, not at the exact moment they plan to arrive. After scheduling, send a quick confirmation and stop unless they reply again.

Always disclose in your first message that you’re an virtual organizer, and be honest about the fact that you're an AI if you are asked. &#x20;
{% endhint %}

### **Collect Email Tool**

Collects and stores an email address for the person in the conversation. Use this when you want the Flow to ask for and save an email — for example, at the end of a survey or intake conversation.

### **Collect Custom Field Tool**

Collects and stores custom field values for the person in the conversation. This is useful for surveys, intake questions, or any scenario where you want the Flow to ask a question and record the answer to a specific field. When adding this tool, hit the "Edit" button to select custom field(s) the Flow should populate, and whether it should be able to overwrite existing values.&#x20;

### **Collect Name Tool**

Collects and stores first name and/or last name for the person in the conversation.

### **Polling Place Lookup Tool**

Finds the nearest polling place using the DNC's I Will Vote API based on a provided address. Useful for voter engagement and GOTV campaigns.

### **Inactivity Follow-up**

Intelligence Nodes can automatically follow up with a friendly nudge when someone stops responding after the AI asks a question. This is configured in the "Procedures" section of the node.

You can customize:

* **Wait time**: How long to wait before following up (e.g., 30 minutes)
* **Max follow-ups**: Maximum number of nudge messages to send (e.g., 2)
* **Follow-up message guidance**: Instructions for how the AI should craft follow-up messages

The default guidance tells the Flow to write short, polite follow-ups that reference the outstanding question. You can customize this to change the AI's behavior — for example, pivoting the conversation to a different topic if someone goes quiet.

### **Collect Address Tool**

Collects and stores a physical address or ZIP code for the person in the conversation. The tool validates and normalizes input using a geocoder, so supporters can type their address naturally and Daisychain will resolve it to a standardized format.

When configuring this tool, you can set a **minimum precision level** depending on what your Flow needs. For example, if you only need a ZIP code or general locality, set a lower precision threshold. If you need an exact street address (e.g., for mail programs or precise district matching), require rooftop-level precision.

The collected address is saved to the person's profile and can be used throughout Daisychain — for example, to target messages by distance radius, look up legislators, or find polling places.

### URL Guardrail

The URL Guardrail helps ensure your AI-powered Flow only shares links you've explicitly approved. When enabled, Daisychain checks every AI response for URLs before sending it. If a URL in the response doesn't match your approved list, the message won't be sent -- instead, the conversation is automatically moved to your Daisychain Inbox for a human to handle.

This prevents the AI from sharing unexpected or hallucinated links with supporters.

#### Enabling the Guardrail

In the Intelligence Node settings, toggle **Enable Guardrail** on. Once enabled, you'll see an **Allowed URL Patterns** field where you can add the URLs you want to permit.

#### Adding Allowed URL Patterns

Enter the beginning of each URL you want to allow. Any URL that starts with one of your patterns will be approved. For example:

* `https://yourorg.com/`  allows all pages on your site, excluding subdomains.
* `https://act.yourorg.com/events/` allows only URLs under that specific path

You can add as many patterns as needed using the **+** button.

#### What Happens When a URL is Blocked

If the AI generates a response containing a URL that doesn't match any of your approved patterns, the message is held and the conversation moves to your Inbox. From there, a team member can review the situation and respond directly.

## Testing Your Flow

Once your Flow is drafted:

1. Click the **Simulator** button
2. Choose a test contact
3. Enter a sample broadcast message (for example, “Can you join a local event?”)
4. Reply like a supporter would and see how the Flow responds

## Connecting a Flow to a Broadcast or Automation

Flows don’t start on their own—they’re triggered when a supporter replies to one of your messages.

To connect a Flow:

1. Go to your [campaigns](campaigns/ "mention") or [automations](../organizing/automations/ "mention") section.&#x20;
2. Under Reply Handling, choose Automated Flow
   1. In Campaigns, this is in Step 2
   2. For Automations, this is available with a "Send a Message" step.&#x20;
3. Select the Flow you created from the dropdown

### Flow Usage

The Flow Usage area lets admins see where a Flow has been used across campaigns, automations, and keywords, and browse or export the conversations generated by each.

To access Flow Usage, open a Flow and press the **Usage** button. From there you can:

* See which campaigns, automations, and keywords are connected to the Flow
* Browse conversations filtered by source
* Export filtered sets of conversations as CSV

## Versions and Revisions

When you update a Flow, Daisychain creates a new version. This ensures that active conversations remain stable while allowing you to iterate and improve.

**How it works:**

* Contacts already in active conversations stay on the version of the Flow they started with
* People added after an update will use the latest version
* You can update instructions, transitions, or nodes at any time without disrupting ongoing conversations

**Why this matters:**

Versioning gives you the flexibility to refine your Flow in an ongoing way. If you discover better phrasing for your instructions or want to add new transitions, you can make those changes knowing that:

* Existing supporters continue their conversations seamlessly with consistent context
* New supporters benefit from your improvements right away
* No conversations are interrupted or broken by your updates

#### Upgrading Active Conversations

When you publish a new version of a Flow that has active conversations, Daisychain will give you the option to update those conversations to use the newly published version of the Flow. If you choose to upgrade:

* Active conversations — including simulated ones — will be moved to the new version of the Flow
* The upgrade handles both Intelligence Nodes and Send a Message Nodes, including configurations for things like Inactivity Follow-Ups.

**Limitations:**

* Conversations that are currently within an Automation Steps Node cannot be upgraded. Daisychain will warn you if this is the case.
* Flows where the structure has fundamentally changed — for example, if a node was fully deleted and replaced with a new one — cannot be upgraded, because Daisychain can't determine where to place existing conversations in the new structure.

If you choose not to upgrade, active conversations stay on their original version, and only new conversations use the latest version.

## Frequently Asked Questions

<details>

<summary><strong>Can a Flow be triggered by inbound keywords or messages?</strong></summary>

Yes! You can connect a Flow to a [keyword](https://daisychain.gitbook.io/help/texting/keywords) so that when someone texts that keyword to your number, the Flow is triggered automatically. To set this up, create or edit a keyword and choose "Flow" as the Response Mode.&#x20;

</details>

<details>

<summary><strong>How do I set up Flows to respond to Campaign replies?</strong></summary>

Campaigns can be configured to ensure that any replies are handled by a Flow. This is managed in Step 2 when creating a Campaign.&#x20;

</details>

<details>

<summary><strong>Do we need to disclose that people are messaging with an AI-powered chatbot?</strong></summary>

We recommend disclosing that it's a chatbot in the first message for transparency and to build trust. You can use whatever language works for you so long as it's clear to the recipient that they are not communicating with a human — examples we've seen include "chatbot", "AI bot", "virtual organizing assistant", "AI-powered voting coach," etc.&#x20;

{% hint style="warning" %}
Some states and jurisdictions may have laws or regulations that require pro-active disclosure when communicating with a chatbot.
{% endhint %}

</details>

<details>

<summary><strong>Will people still engage if they know it's a bot?</strong></summary>

Pilot programs show people are willing to engage with Flows even after disclosure. In some cases, using Flows leads to longer conversations and deeper engagement than human texters – primarily due to speed of response.

</details>

<details>

<summary><strong>Does the AI model train on our conversation data?</strong></summary>

The AI models Daisychain uses do not train on client data accessed through their API. Your conversations remain private.

</details>

<details>

<summary><strong>How can I  monitor conversations happening in a Flow?</strong></summary>

Conversations appear in the "Completed" tab where you can review the full conversation history. You have visibility into all AI interactions.

</details>

<details>

<summary><strong>Can someone from my team jump in and take over from the AI?</strong></summary>

Yes. Staff can manually jump into any conversation at any time by sending a message in the conversation manually from the Inbox or a Person's profile. This will automatically end the AI Flow. This human handoff capability ensures you maintain control.

</details>
