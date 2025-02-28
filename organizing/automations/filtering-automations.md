---
description: You can filter automations so they only run when specific criteria are met.
icon: square-bolt
---

# Filtering Automations

[Automations](./) run on all actions by default, but after you choose a trigger you have the option of adding filters to only run the automation when it matches certain specified conditions -- such as signups on specific pages, or donations over certain dollar amounts.

Filtering your triggers requires first selecting the "Filter Automation" option.

From there, you can:

*   Write your filter in plain English -- something like "donors who gave more than $100 and live in Ohio." Automation filters are expressed using the [JMESPath query language](https://jmespath.org/), but a little help from Daisychain's AI assistant prevents you from having to learn or understand how to code these filters manually. After writing your filter in plain English, just click the "Convert to JMESPath" button to try out Daisychain's AI Assistant

    <figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
* Write or edit the JMESPath code directly in the "JMESPath Expression" box.\
  ​
* Click the link to the "JMESPath Playground" where you can test out your JMESPath code.

Daisychain's AI assistant currently works to create filters for ActBlue, EveryAction, and Zapier. More options coming soon! The AI assistant is also not 100% consistent, and automations using AI-generated JMESPath should be tested carefully.&#x20;

Below are are few examples of JMESPath code, but please reach out to support if you have questions about how to use this feature, or need help writing JMESPath code to filter your triggers.

#### **Only run automation if a person has (or doesn't have) a particular tag**

To only run an automation if someone **DOESN'T** have a particular tag, use the following code.

```
!person.tag\_list [?contains(@, 'volunteer-leader')] 
```

To only run an automation if someone DOES have a particular tag, use the following code:

```
person.tag\_list [?contains(@, 'volunteer-leader' )] 
```

Note that this needs to be a tag’s “unique identifier.” In the example above, the original tag was “Volunteer Leader.” A tag’s unique identifier is always lowercase and don’t have any spaces. Any spaces in tags should be replaced by dashes.

#### **Action Network: only run automation when a specific form is submitted**

```
action."osdi:submission"."\_links"."osdi:form".href == 'https://actionnetwork.org/api/v2/forms/416c031d-7c9d-4147-90cf-d9p0d5rc18e9'
```

When using this code, you'll need to swap in the appropriate URL for your form. This can be obtained by navigating to manage your action in Action Network, scrolling down, and copying the link that says "API ENDPOINT & FORM ID" section, like this:

#### **EveryAction: only run automation when a specific form is submitted**

```
action.form.form\_id == `1234567`
```

When using this code, you'll need to swap in the appropriate Form ID for your EveryAction form.

#### **ActBlue: only run automation when a donation is above a specific amount**

```
action.contribution.totalAmount.to\_number(@) > `100`
```

&#x20;(When using this code, you can swap in whatever minimum amount you choose -- just replace `100` with any other number.) &#x20;

#### **Mobilize: only run automation on specific event**

```
action.event.external\_id == '1234'
```

&#x20;(When using this code, you can swap in whatever your numerical event ID is.) &#x20;
