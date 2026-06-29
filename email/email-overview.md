---
description: How email works in Daisychain.
icon: square-envelope
---

# Email Overview

Daisychain supports sending personalized, mobile-friendly emails as part of [automations](../organizing/automations/ "mention"). Daisychain doesn't currently support one-off email broadcasts or standalone campaigns — emails can only be sent through automation steps.

To get started, you’ll need to [configure your domain](email-configuration.md) and [create your message](../creating-emails.md) when building an automation. &#x20;

#### Unsubscribes and Deliverability

Daisychain's built-in layouts include an unsubscribe link automatically. If you build a custom layout, be sure to keep the `{% unsubscribe_url %}` tag in your footer so recipients can always opt out. If you have an integration with [action-network.md](../integrations/action-network.md "mention"), unsubscribes are synced back, helping keep your lists clean and compliant.
