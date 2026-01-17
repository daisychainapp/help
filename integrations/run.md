---
description: How to Integrate the Daisychain with Run!
icon: person-running
---

# Run

RUN is an easy-to-use campaign website builder for Democrats and advocacy organizations. When you connect RUN to Daisychain, form submissions from your RUN website flow directly into your Daisychain account, where you can trigger automations, send follow-up messages, and organize your supporters.

### Setting Up the Integration

The RUN integration is configured from within your RUN account. For detailed setup instructions, see [RUN's Daisychain integration guide](https://help.designedtorun.com/en/articles/8437073-daisychain-integration).

Here's a quick overview:

1. **Get your Daisychain API key.** In Daisychain, go to Settings > API Keys and click "Add API Key."
2. **Connect to Daisychain in RUN.** In the RUN form builder, click to add a destination, select Daisychain, and enter your API key. Confirm it's connecting correctly under "Status" after you save.
3. **Enable the integration on each form.** In RUN's form builder, check the "Enable" checkbox next to the Daisychain destination for every form you want to sync.

### Custom Fields

To capture additional data beyond standard contact info, create [custom fields](../managing-data/custom-fields.md) in Daisychainfirst. Then in RUN's form builder, add a custom field and select the corresponding Daisychain field from the dropdown.

### Triggering Automations from RUN Form Submissions

When someone submits a form on your RUN website, you can use [automations](../organizing/automations/ "mention") to send them a welcome email, add them to a Pathway, assign them to an organizer, or trigger any other Daisychain automation.

#### Creating an Automation for RUN Submissions

1. Go to Settings > Automations and click "Add"
2. Select **"Record Person Action"** as the trigger
3. Add an [Automation Filter](../organizing/automations/filtering-automations.md) to target only RUN form submissions:

```
   action.type == "run-form"
```

4. Add your automation steps (send email, add tag, create card, etc.)

