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

    <figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
The AI assistant is not 100% accurate, and automations using AI-generated JMESPath should be tested carefully. Daisychain's AI assistant currently works to create filters for ActBlue, EveryAction, and Zapier. More options coming soon!
{% endhint %}

* Write or edit the JMESPath code directly in the "JMESPath Expression" box.

### Testing Filters with the JMESPath Playground

Before saving your filter expression in an automation, you can test it using Daisychain’s built-in "JMESPath Playground". This tool lets you preview whether a given filter expression will match recent incoming actions.

To access the JMESPath Playground where you can test out your JMESPath code, follow these steps:

1. Create an automation, pick your trigger, and select the "Filter automation to actions that meet specific criteria."
2.  From there, click the JMESPath Playground link, highlighted below:<br>

    <figure><img src="../../.gitbook/assets/image (49) (1).png" alt=""><figcaption></figcaption></figure>
3. Find a recent action that matches the filter you're creating.
4. Paste or write your filter expression in the editor.
5.  Click Test to see if the expression matches the example data. If the filter fails to match, the playground will show `Match: false`, so you can tweak your expression until returns `Match: true` The status will display below the window, next to the "Test" button:

    <figure><img src="../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

### JMESPath Queries

Actions that trigger Dasisychain automations have JSON representations of the activity on an external system or within Daisychain that triggered the automation. For Actblue donations this JSON representation might include the details of the contribution, for mobilize the event and timeslot that the person RSVP'd to. For automations triggered via the Daisychain actions API, this JSON is provided by the system that calls the Daisychain API in the API submission.

Automations can be filtered by querying the JSON representation of the activity using JMESPath. If the JMESPath query you write returns an empty or null result we do not run the automation. If the JMESPath query returns part of the JSON document or a true value, we consider it a match and allow the automation to run.

This allows extremely powerful expressions to be written to restrict each automation you setup to specific activity. It also means that JMESPath filters need to be carefully designed and tested in order to ensure they work as you intended.

### JMESPath Extensions

We've extended the official JMESPath standard to add additional functions to allow for querying based on date and time. These functions are particularly useful for working with Event RSVPs and recurring donations.

| Function                  | Description                                                                                         |
| ------------------------- | --------------------------------------------------------------------------------------------------- |
| `current_datetime()`      | Returns the current DateTime as a string in ISO8601 format                                          |
| ``seconds_from_now(`2`)`` | The DateTime that is the specified number of integer seconds from now as a string in ISO8601 format |
| ``minutes_from_now(`5`)`` | The DateTime that is the specified number of integer minutes from now as a string in ISO8601 format |
| ``hours_from_now(`3`)``   | The DateTime that is the specified number of integer hours from now as a string in ISO8601 format   |
| ``days_from_now(`1`)``    | The DateTime that is the specified number of integer days from now as a string in ISO8601 format    |
| ``weeks_from_now(`2`)``   | The DateTime that is the specified number of integer weeks from now as a string in ISO8601 format   |
| ``months_from_now(`1`)``  | The DateTime that is the specified number of integer months from now as a string in ISO8601 format  |
| ``years_from_now(`1`)``   | The DateTime that is the specified number of integer years from now as a string in ISO8601 format   |
| ``seconds_ago(`5`)``      | The DateTime that is the specified number of integer seconds ago as a string in ISO8601 format      |
| ``minutes_ago(`10`)``     | The DateTime that is the specified number of integer minutes ago as a string in ISO8601 format      |
| ``hours_ago(`2`)``        | The DateTime that is the specified number of integer hours ago as a string in ISO8601 format        |
| ``days_ago(`1`)``         | The DateTime that is the specified number of integer days ago as a string in ISO8601 format         |
| ``weeks_ago(`1`)``        | The DateTime that is the specified number of integer weeks ago as a string in ISO8601 format        |
| ``months_ago(`1`)``       | The DateTime that is the specified number of integer months ago as a string in ISO8601 format       |
| ``years_ago(`1`)``        | The DateTime that is the specified number of integer years ago as a string in ISO8601 format        |

While JSON does not have native date handling, the ISO8601 Date Time string format is lexigraphically sortable, and we use 8601 format throughout Daisychain.

This allows us to write date comparisons to the specified date.

For eg, to filter to mobilize attendances to event timeslots that are more than 4 days from now, you could write an expression like this.

```
action.timeslot.start_at > days_from_now(`4`)
```

### Example Automation Filters

Below are are few examples of JMESPath code, but please reach out to support if you have questions about how to use this feature, or need help writing JMESPath code to filter your triggers.

#### **Only run automation if a person has (or doesn't have) a particular tag**

To only run an automation if someone **DOESN'T** have a particular tag, use the following code.

```sql
!person.tag_list [?contains(@, 'volunteer-leader')]
```

To only run an automation if someone DOES have a particular tag, use the following code:

```sql
person.tag_list [?contains(@, 'volunteer-leader' )]
```

Note that this needs to be a tag’s “unique identifier.” In the example above, the original tag was “Volunteer Leader.” A tag’s unique identifier is always lowercase and don’t have any spaces. Any spaces in tags should be replaced by dashes.

#### **Action Network: only run automation when a specific form is submitted**

{% code overflow="wrap" %}
```sql
action."osdi:submission"."_links"."osdi:form".href == 'https://actionnetwork.org/api/v2/forms/416c031d-7c9d-4147-90cf-d9p0d5rc18e9'
```
{% endcode %}

When using this code, you'll need to swap in the appropriate URL for your form. This can be obtained by navigating to manage your action in Action Network, scrolling down, and copying the link that says "API ENDPOINT & FORM ID" section.

#### **EveryAction: only run automation when a specific form is submitted**

```sql
action.form.short_code == 'yHXCdSkQGU2-zKQijim5aw2'
```

When using this code, you'll need to swap in the appropriate Form ID for your EveryAction form.

#### **ActBlue: only run automation when a donation is above a specific amount**

```sql
action.contribution.totalAmount.to_number(@) > `100`
```

When using this code, you can swap in whatever minimum amount you choose -- just replace `100` with any other number.

#### **Mobilize: only run automation on specific event**

```sql
action.event.external_id == '123456'
```

When using this code, you can swap in whatever your numerical event ID is.

#### **Mobilize: only run automation for a given event type**

```sql
action.event.event_type == 'EVENT_TYPE'
```

#### **Zapier: only run automation on a specific Zap ID**

```sql
action.zap.id == '123456789' || action.zap.id == `123456789`
```

When using this code, you can swap in whatever your numerical Zap ID is.
