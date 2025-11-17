---
description: Flows let you automate multi-step conversations with supporters.
hidden: true
icon: code-branch
---

# Flows (Beta)

{% hint style="warning" %}
**Beta Feature**

Flows are _off_ by default. If you have an active Daisychain subscription and want to try Flows, just reach out to help@daisychain.app.&#x20;

And if you run into issues or have ideas for improvement, we’d love to hear them.
{% endhint %}

## What is a Flow?

A **Flow** is a structured conversation that can be triggered when a supporter replies to a message sent through [campaigns](campaigns/ "mention") or [automations](../organizing/automations/ "mention"). You can think of it as a branching conversation tree: it starts with a supporter’s incoming reply, and your outgoing messages can change based on what your supporters say.

Flows can:

* Ask follow-up questions
* Respond with personalized messages
* Look up legislator info
* Schedule messages for later
* Nudge non-responsive people to reply (coming soon)
* Update data fields (coming soon)

## Creating a New Flow

1. **Go to the Flows tab**\
   From your campaign dashboard, click the Flows icon in the left-hand sidebar.
2. **Click "New Flow"**\
   Give your Flow a name. You can always rename it later.
3. **Add your first Node**\
   A Flow starts when a supporter replies to your broadcast message. Click the green **+** button to add a Node.

***

## Node Types

When adding a Node, you’ll choose one of three types:

### Intelligence Node (AI-powered)

Let the AI interpret the supporter’s message and respond using your custom instructions.

* You can choose the AI model — for example, GPT-5, _Claude Sonnet 4.5_. Note that the newest and most advanced models will take a longer time to respond.&#x20;
* You can toggle whether the AI should send a reply message or just analyze silently. (For now, this toggle is always on.)
* The AI will have access to all [standard-fields.md](../managing-data/standard-fields.md "mention") and [custom-fields.md](../managing-data/custom-fields.md "mention") associated with a given person, and can use the data stored in those fields to inform the conversation.&#x20;
* Currently, the AI does not have access to [notes.md](../organizing/notes.md "mention") associated with that Person or actions from the Person's timeline.&#x20;
* Your custom instructions should provide clarity on the role of the AI, how it should respond, what capabilities it does (or doesn't) have, and any guardrails. Example below.&#x20;

{% hint style="success" %}
**Best Practices For Using Intelligence Nodes**

* Keep instructions short and clear — AI performs better with direct guidance
* Always disclose that an AI or "virtual organizer" is generating messages
* [Test your Flow](flows-beta.md#testing-your-flow) in the the Simulator before going live
{% endhint %}

{% hint style="info" %}
**Example Instructions for an Intelligence Node**

You are a friendly community organizer helping supporters decide whether to attend an upcoming event.

The event is a community rally for climate action, focused on pressuring City Council to pass the Affordable Clean Energy Plan — a proposal that would cut citywide carbon emissions by 40% by 2030, expand access to renewable energy for low-income residents, and create hundreds of local green jobs. It takes place on Saturday, October 12th at 3 PM at Springfield Park. There will be speakers, music, and snacks. The vibe is family-friendly and welcoming to newcomers.

Your goal is to answer questions about the event and the Affordable Clean Energy Plan, explain why it matters, and encourage people to come — without being pushy.

Use a warm, supportive tone.

You cannot register people yourself or send emails, so never promise that. If someone seems unsure, offer more details (like the location, time, what’s on the agenda, or highlights of the plan) or ask what would help them decide.

Always disclose in your first message that you’re an virtual organizer, and be honest about the fact that you're an AI if you are asked. &#x20;

If you don't know the answer to a question, disclose that you don't know. You can link to the page with more info here: [http://springfieldcleanenergy.com/](http://springfieldcleanenergy.com/)&#x20;
{% endhint %}

#### Tools

Tools extend what an Intelligence Node can do inside a Flow. They allow the AI to take specific actions rather than just sending a message. For example, a tool might look up data, create a tag, or schedule a follow-up.

Each Intelligence Node can be configured with one or more tools, depending on what you want the Flow to accomplish. Tools are selected when configuring the node, below the model and instruction settings.

**Legislative Lookup Tool**

The Legislative Lookup tool lets your Intelligence Node automatically identify federal elected officials in the US based on a person's location. This is especially useful in advocacy campaigns so you can help a person look up their local representative without sending them to a separate lookup tool.&#x20;

When using this tool, you'll want to provide overall instructions that specify what information is needed to look up their elected official. For the US Senate, you only need the person's state. For the US house, you'll need a full address.&#x20;

{% hint style="info" %}
**Sample Instructions for an Intelligence Node using the Legislative Lookup tool**

You are a friendly community organizer helping supporters take action to stop House Bill 123, a proposed federal law that would restrict clean energy access and reduce funding for solar power.

Your goal is to help people understand why the bill matters, identify their elected officials using the Legislative Lookup tool, and encourage them to contact those officials.

When someone provides their address and state, use the Legislative Lookup tool to find their representatives and their contact inco. If they don’t include their full address, ask politely so you can make sure their message reaches the right officials.

Keep your tone warm, clear, and factual. Always disclose in your first message that you’re an virtual organizer, and be honest about the fact that you're an AI if you are asked.   If you don’t know an answer, say so and share the campaign link above for more info.
{% endhint %}

**Scheduler Tool**&#x20;

The Scheduler Tool lets the  Flow automatically schedule a follow-up SMS message at a specific date and time. This is especially useful when you want to check back in about a commitment someone made or an action they are planning to take (like attending a meeting or showing up to an event) without requiring manual follow-up.

When using this tool, you’ll want to guide the person to share when they’re planning to take the action. Once they give a date or time, the Scheduler Tool can trigger a reminder message at that exact moment. For best results with teh schedule tool, include a section of your Instructions that invokes it by name ("scheduler tool") and be specific about how you want it to behave.&#x20;

{% hint style="info" %}
**Sample Instructions for an Intelligence Node using the Scheduler tool**

You are virtual organizing assistant helping the contact make a plan to visit their congressional office. Guide them to pick a day for their visit, confirm the plan, and then schedule a reminder for the morning of that day.

Ask one question at a time. Accept any reply that clearly indicates intention or timing. If their answer is unclear, ask one brief clarifying question.&#x20;

Once they give a usable date, use the scheduler tool to set a follow-up message for the morning of that date, not at the exact moment they plan to arrive. After scheduling, send a quick confirmation and stop unless they reply again.

Always disclose in your first message that you’re an virtual organizer, and be honest about the fact that you're an AI if you are asked. &#x20;
{% endhint %}

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

### Automation Steps Node _(coming soon)_

Perform actions like applying [tags.md](../managing-data/tags.md "mention"), adding people to [pathways.md](../organizing/pathways.md "mention"), making [assignments.md](../organizing/assignments.md "mention"), sending [emails](../email/email-overview.md), and more.&#x20;

{% hint style="danger" %}
While you can currently create an Automation Steps node, it will not work until further updates are made.
{% endhint %}

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
