---
description: >-
  Record answers that change over time, with full history of who recorded the
  answer and when.
icon: comments-question-check
---

# Questions

Questions let you ask and record answers that may change over time — like support scores, volunteer availability, or issue priorities.

### Creating Questions

1. Go to **Settings > People > Questions**
2. Click **Add Your First Question** (or **Add Question** if you already have questions)
3. Enter your **Question** text (this is what users will see when recording answers)
4. Optionally add **Helper text** with instructions that appear below the question
5. Choose an **Answer type**:
   * **Short text**: Brief free-form responses
   * **Long text**: Longer responses with more space
   * **Multiple choice**: Select one option from a list
   * **Dropdown**: Select one option from a dropdown menu
   * **Yes/No**: Simple binary choice
   * **Number**: Numeric values only
   * **Date**: Date picker
6. Optionally assign to a **Question group** to organize related questions together
7. Click **Save Question**

### Question Groups

Question groups let you organize related questions so they display together when recording answers. For example, you might group all your Voter ID questions or all your volunteer intake questions.

To create a new group, click **+ New** next to the Question group dropdown when adding or editing a question.

### Recording Answers

You can record answers to questions from a person's profile in the Questions tab. Each answer is saved with:

* The answer value
* The user who recorded it
* The date and time it was recorded

Previous answers are preserved, so you can see how responses have changed over time.

### Questions vs. [Custom Fields](custom-fields.md)

Both features let you store data about people beyond standard fields like name and email. The key differences:

|                      | Custom Questions                                      | Custom Fields                                             |
| -------------------- | ----------------------------------------------------- | --------------------------------------------------------- |
| **Values over time** | Same question can be answered multiple times          | Stores only one value (overwrites previous)               |
| **History tracking** | Records who answered and when                         | No history                                                |
| **Best for**         | Support scores, survey responses, recurring check-ins | Static attributes like preferred language or T-shirt size |
| **Use in messages**  | Not available for personalization                     | Can be inserted into messages                             |

**Example:** If you're tracking voter support on a 1-5 scale, use a Question. You might ask the same person their support level in March, then again in October -- and you'll want to see both answers and how they changed. If you're storing someone's preferred pronoun, use a Custom Field since you only need the current value.

{% hint style="info" %}
Read more about the differences between three custom data types in the [tags-vs.-custom-fields.md](tags-vs.-custom-fields.md "mention")article.&#x20;
{% endhint %}
