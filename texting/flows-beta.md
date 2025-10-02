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

### What is a Flow?

A **Flow** is a structured conversation that can be triggered when a supporter replies to a message sent through [campaigns](campaigns/ "mention") or [automations](../organizing/automations/ "mention"). You can think of it as a branching conversation tree: it starts with a supporter’s incoming reply, and your outgoing messages can change based on what your supporters say.

Flows can:

* Ask follow-up questions
* Respond with personalized messages
* Look up legislator info (coming soon)
* Schedule messages for later (coming soon)
* Update data fields (coming soon)

### Creating a New Flow

1. **Go to the Flows tab**\
   From your campaign dashboard, click the Flows icon in the left-hand sidebar.
2. **Click "New Flow"**\
   Give your Flow a name. You can always rename it later.
3. **Add your first Node**\
   A Flow starts when a supporter replies to your broadcast message. Click the green **+** button to add a Node.

***

### Node Types

When adding a Node, you’ll choose one of three types:

#### Send a Message Node

Send a quick response back to the supporter — no logic, no AI. Currently, the send message node will only send a single message, and doesn't have [#node-transitions-coming-soon](flows-beta.md#node-transitions-coming-soon "mention"). Think of it like an "autoresponder", in a "Send a Message" node will always (and repeatedly) send the same message.&#x20;

#### Intelligence Node (AI-powered)

Let the AI interpret the supporter’s message and respond using your custom instructions.

* You can choose the **AI model** (for example, GPT-5, _Claude Sonnet 4.5_) after creating it.&#x20;
* You can toggle whether the AI should **send a reply message** or just analyze silently. (For now, this toggle is always on.)
* The AI will have access to all [standard-fields.md](../managing-data/standard-fields.md "mention")and [custom-fields.md](../managing-data/custom-fields.md "mention")associated with a given person, and can use the data stored in those fields to inform the conversation.&#x20;
* Currently, the AI does not have access to [notes.md](../organizing/notes.md "mention") associated with that Person or actions from the Person's timeline.&#x20;
* Your custom instructions should provide clarity on the role of the AI, how it should respond, what capabilities it does (or doesn't) have, and any guardrails. Example below.&#x20;

{% hint style="success" %}
**Sample Instructions for an Intelligence Node**

You are a friendly community organizer helping supporters decide whether to attend an upcoming event.

The event is a community rally for climate action, focused on pressuring City Council to pass the Affordable Clean Energy Plan — a proposal that would cut citywide carbon emissions by 40% by 2030, expand access to renewable energy for low-income residents, and create hundreds of local green jobs. It takes place on Saturday, October 12th at 3 PM at Springfield Park. There will be speakers, music, and snacks. The vibe is family-friendly and welcoming to newcomers.

Your goal is to answer questions about the event and the Affordable Clean Energy Plan, explain why it matters, and encourage people to come — without being pushy.

Use a warm, supportive tone.

You cannot register people yourself or send emails, so never promise that. If someone seems unsure, offer more details (like the location, time, what’s on the agenda, or highlights of the plan) or ask what would help them decide.

Always disclose in your second message that you’re an virtual organizer, and be honest about the fact that you're an AI if you are asked. &#x20;

If you don't know the answer to a question, disclose that you don't know. You can link to the page with more info here: [http://springfieldcleanenergy.com/](http://springfieldcleanenergy.com/)&#x20;
{% endhint %}

#### Automation Steps Node _(coming soon)_

Perform actions like applying [tags.md](../managing-data/tags.md "mention"), adding people to [pathways.md](../organizing/pathways.md "mention"), making [assignments.md](../organizing/assignments.md "mention"), and more.&#x20;

### Node Transitions (Coming Soon)

{% hint style="danger" %}
While Transitions currently appear in the Flows UI, they do not currently work.&#x20;
{% endhint %}

Transitions let your Flow decide what node to proceed to next based on how someone replies.

#### How to Add a Transition&#x20;

Transitions only work with Intelligence Nodes. If you're using an Intelligence Node, you can add one or more Transitions.&#x20;

1. Click the "Add Transition" Button
2. Give it a short name (like “Wants to attend the event”)
3. Describe the condition and provide a few examples of what the reply should sound like. (Example below)

{% hint style="info" %}
**Example Transition Instructions**

The user is making a commitment to take an action. This includes messages like:

* 'I will go to the rally'
* 'I will ask my friends to join'
* Any variations where the user is committing to do something.&#x20;

Return "true" if the message is making an explicit commitment to attend the rally, "false" if they are not.
{% endhint %}

The AI will check each transition in order and follow the first one that matches.&#x20;

### Testing Your Flow

Once your Flow is drafted:

1. Click the **Simulator** button
2. Choose a test contact
3. Enter a sample broadcast message (for example, “Can you join a local event?”)
4. Reply like a supporter would and see how the Flow responds

This helps preview how your instructions and nodes work together.

### Connecting a Flow to a Broadcast or Automation

Flows don’t start on their own—they’re triggered when a supporter replies to one of your messages.

To connect a Flow:

1. Go to your [campaigns](campaigns/ "mention") or [automations](../organizing/automations/ "mention")section.&#x20;
2. Under Reply Handling, choose Automated Flow
   1. In Campaigns, this is in Step 2
   2. For Automations, this is available with a "Send a Message" step.&#x20;
3. Select the Flow you created from the dropdown

### Best Practices

* Keep instructions short and clear — AI performs better with direct guidance
* Always disclose that an AI or "virtual organizer" is generating messages
* Use the Simulator before going live
* Avoid dead ends: have the AI ask a follow-up or offer next steps
* Treat Flows as an assist (not a replacement) for real conversations
