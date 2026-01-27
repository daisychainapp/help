---
description: >-
  Learn the key differences between Tags, Questions, and Custom Fields in
  Daisychain and understand how to effectively use each to manage and engage
  your contacts.
icon: lightbulb
---

# Tags vs. Custom Fields vs. Questions

### Quick Comparison

|                                     | Tags                    | Custom Fields                        | Questions                                                |
| ----------------------------------- | ----------------------- | ------------------------------------ | -------------------------------------------------------- |
| **Best for**                        | Simple labels           | Static attributes                    | Data that changes over time                              |
| **Example**                         | "Volunteer", "Donor"    | "Preferred Language", "T-Shirt Size" | "Support Score", "Volunteer Availability"                |
| **Tracks who recorded it and when** | No                      | No                                   | Yes                                                      |
| **Easy to remove/change**           | Yes                     | Moderately                           | History is preserved — new answers don't delete old ones |
| **Filter People list**              | Yes (with AND/OR logic) | Limited (single field, exact match)  | No                                                       |
| **Filter Inbox**                    | Yes                     | No                                   | No                                                       |
| **Insert into messages**            | No                      | Yes                                  | No                                                       |

### Tags Overview

Tags are simple labels you can add or remove from people. They're best for binary information —  someone either has the tag or they don't.

**Use Tags when you need to:**

* Quickly add and remove labels
* Filter the Inbox by a specific criterion
* Filter the People list using AND/OR logic across multiple tags

**Examples:** "Volunteer", "Donor", "Spanish-Speaker", "Event-Attendee"

{% hint style="info" %}
Learn more in the [tags.md](tags.md "mention") article.&#x20;
{% endhint %}

### Custom Fields Overview

Custom Fields store a single value for each person. When you update a Custom Field, it overwrites the previous value — there's no history.

**Use Custom Fields when you need to:**

* Store static information that rarely changes
* Insert personalized content into messages (e.g. "Hi \{{ person.preferred\_name \}}")
* Record structured data like numbers or dropdown selections

**Examples:** "Preferred Language", "T-Shirt Size", "Employer", "Congressional District"

{% hint style="info" %}
Learn more in the [custom-fields.md](custom-fields.md "mention") article.&#x20;
{% endhint %}

### Questions Overview

Questions let you record answers that change over time. Each answer is saved with who recorded it and when — so you can track how someone's responses evolve.

**Use Questions when you need to:**

* Ask the same question multiple times over weeks or months
* See a history of how answers have changed
* Know which team member recorded each answer

**Examples:** "Support Score (1-5)", "Will you volunteer this weekend?", "Top issue priority"

{% hint style="info" %}
Learn more in the [questions.md](questions.md "mention") article.&#x20;
{% endhint %}
