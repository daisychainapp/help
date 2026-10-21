---
description: >-
  Split people into random groups with a custom field, for A/B tests,
  holdout groups, and experiments that run across many campaigns.
icon: shuffle
---

# Random Assignment

Daisychain can write a random number into a [custom field](custom-fields.md) for everyone on a list. If you pick a range of 1 to 2, every person gets a 1 or a 2, and you have two random groups you can filter and target separately.

The groups stay the same until you change them. That makes random assignment useful for things a single campaign can't do on its own:

* **Longitudinal experiments.** Keep the same people in the same group across weeks or months of sends, then compare the groups. For example, text Group A weekly and Group B every other week, and see which group donates more, opts out less, or shows up to more events.
* **Holdout groups.** Leave a random group out of a program entirely, and compare it with the people who received it to measure what the program actually changed.
* **Rotating sends.** Text Group A on one send and Group B on the next, so nobody hears from you every time.
* **Experiments outside texting.** Use the groups with [pathways](../organizing/pathways.md), assignments, or anything else you can target with a filter.

{% hint style="info" %}
To test which message works best in a single campaign, use the campaign's built-in [A/B Testing](../texting/campaigns/a-b-testing.md) instead. It picks a fresh random sample for each campaign. Random assignment is for groups that need to stay fixed across many campaigns.
{% endhint %}

### Assigning Random Numbers

1. **Create a field for the number.** Go to **Settings**, then **Fields**, and click **Add**. Give it a name like "Random Group" and set the Field Type to **Number**.
2. **Choose who to include.** Go to **People**. To split everyone in your account, skip this step. To split a subset, use [filters](filtering-people.md) to narrow the list, for example **Filter**, then **CSV Import**, to pick a single upload.
3. **Select everyone.** Check the box in the top-left corner of the list, then click the **Select all** link that appears, so you select everyone and not just the first page.
4. **Assign the numbers.** Click **Update Custom Field** and open the **Randomly Assign** tab. Choose your field, set **Min** and **Max** (for example, 1 and 2 for two groups), and click **Apply**.

The update runs in the background, and you'll see a notification when it's finished. Each person gets a whole number between the Min and Max, including both ends.

### Targeting Each Group

1. On **People**, click **Filter**, choose **Custom Fields**, pick your field, choose **is**, and enter **1**.
2. Click **Save Filter** and name it something like "Group A".
3. Repeat with **2** and save it as "Group B".

When you set up a [campaign](../texting/campaigns/), choose one of these saved filters as the **Audience**. You can also put a group in the **Don't send to** menu to hold it out.

### Tips

* **Groups are close to even, not exactly even.** Each person's number is picked independently, so a two-way split of 1,000 people might come out as 489 and 511.
* **Use a wider range for more groups.** A range of 1 to 4 gives four groups. A range of 1 to 10 gives ten groups of about 10% each, so filtering for **is 1** gives you a 10% holdout.
* **Keep groups stable when people join.** Running Randomly Assign again overwrites the number for everyone you select, which reshuffles your groups. To give new people a group without changing anyone else's, filter for your field **has no value**, select everyone, and run Randomly Assign on just them.
* **Use a new field for each experiment.** If you start a new experiment, create a new field rather than reusing an old one, so you can still filter by the earlier groups when you look back at their results.
* **Decide what you'll measure before you start,** and give the experiment enough sends for the difference between groups to show up.

{% hint style="warning" %}
Bulk updates are available to Admins and Managers. See [Users and Roles](../settings/users-and-roles.md).
{% endhint %}
