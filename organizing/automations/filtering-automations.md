---
description: You can filter automations so they only run when specific criteria are met.
icon: square-bolt
---

# Filtering Automations

[Automations](./) run on all actions by default, but after you choose a trigger you have the option of adding filters to only run the automation when it matches certain specified conditions -- such as signups on specific pages, or donations over certain dollar amounts.

### How to Create an Automation Filter

Filtering your triggers requires first selecting the "Filter Automation" option.

From there, you can:

*   Write your filter in plain English -- something like "donors who gave more than $100 and live in Ohio." Automation filters are expressed using the [JMESPath query language](https://jmespath.org/), but a little help from Daisychain's AI assistant prevents you from having to learn or understand how to code these filters manually. After writing your filter in plain English, just click the "Convert to JMESPath" button to try out Daisychain's AI Assistant

    <figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
The AI assistant is not 100% accurate, and automations using AI-generated JMESPath should be tested carefully. Daisychain's AI assistant currently works to create filters for ActBlue, EveryAction, and Zapier. More options coming soon!&#x20;
{% endhint %}

* Write or edit the JMESPath code directly in the "JMESPath Expression" box.

### Testing Filters with the JMESPath Playground

Before saving your filter expression in an automation, you can test it using Daisychain’s built-in "JMESPath Playground". This tool lets you preview whether a given filter expression will match recent incoming actions.

To access the JMESPath Playground where you can test out your JMESPath code, follow these steps:

1. Create an automation, pick your trigger, and select the "Filter automation to actions that meet specific criteria."
2.  From there, click the JMESPath Playground link, highlighted below:\
    \


    <figure><img src="../../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>
3. Find a recent action that matches the filter you're creating.&#x20;
4. Paste or write your filter expression in the editor.
5.  Click Test to see if the expression matches the example data. If the filter fails to match, the playground will show `Match: false`, so you can tweak your expression until returns `Match: true` The status will display below the window, next to the "Test" button:\


    <figure><img src="../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

### Example Automation Filters

Below are are few examples of JMESPath code, but please reach out to support if you have questions about how to use this feature, or need help writing JMESPath code to filter your triggers.

#### **Only run automation if a person has (or doesn't have) a particular tag**

To only run an automation if someone **DOESN'T** have a particular tag, use the following code.

```
!person.tag_list [?contains(@, 'volunteer-leader')] 
```

To only run an automation if someone DOES have a particular tag, use the following code:

```
person.tag_list [?contains(@, 'volunteer-leader' )] 
```

Note that this needs to be a tag’s “unique identifier.” In the example above, the original tag was “Volunteer Leader.” A tag’s unique identifier is always lowercase and don’t have any spaces. Any spaces in tags should be replaced by dashes.

#### **Action Network: only run automation when a specific form is submitted**

```
action."osdi:submission"."_links"."osdi:form".href == 'https://actionnetwork.org/api/v2/forms/416c031d-7c9d-4147-90cf-d9p0d5rc18e9'
```

When using this code, you'll need to swap in the appropriate URL for your form. This can be obtained by navigating to manage your action in Action Network, scrolling down, and copying the link that says "API ENDPOINT & FORM ID" section.

#### **EveryAction: only run automation when a specific form is submitted**

```
action.form.short_code == 'yHXCdSkQGU2-zKQijim5aw2'
```

When using this code, you'll need to swap in the appropriate Form ID for your EveryAction form.

#### **ActBlue: only run automation when a donation is above a specific amount**

```
action.contribution.totalAmount.to_number(@) > `100`
```

&#x20;(When using this code, you can swap in whatever minimum amount you choose -- just replace `100` with any other number.) &#x20;

#### **Mobilize: only run automation on specific event**

```
action.event.external_id == '123456'
```

&#x20;(When using this code, you can swap in whatever your numerical event ID is.)&#x20;

**Mobilize: only run automation for a given event type**

```
action.event.event_type == 'EVENT_TYPE'
```
