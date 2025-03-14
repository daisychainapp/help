---
description: How to integrate Daisychain with ControlShift
icon: hand-fist
---

# ControlShift

[ControlShift](https://www.controlshiftlabs.com/) is a toolset used to put people at the center of campaigns through distributed events, local groups, and member-led petitions.

You can use Daisychain to create a high-touch organizing workflow to support ControlShift petition-creators. When you integrate Daisychain and ControlShift, a few things happen:

* When new petitions created on ControlShift, a new card will be created on a dedicated Daisychain [Pathway](../organizing/pathways.md) that has a special "power-up."\
  ​
* Card representing petitions will have a power-up containing:
  * Petition name
  * Link to the petition on ControlShift
  * Current signature count
  * Moderation status\

* If a petition has a ["Mentor" in ControlShift](https://support.controlshiftlabs.com/hc/en-us/articles/202041276-Moderation-Workflow-for-New-Petitions), there will be an attempt to sync it with an [Assignment](../organizing/assignments/) in Daisychain, and vice-versa.

**Here's how to setup the integration between Daisychain and ControlShift:**

1. In ControlShift, navigate to Settings > Integrations > REST API Apps\
   ​
2. Give your application a name (like "Daisychain") and a Redirect URI (use "urn:ietf:wg:oauth:2.0:oob"), and hit the "Add" button.​\
   ​
3. In a new browser tab, go to your Daisychain account. Navigate to Settings > Integrations > ControlShift (Add). You'll see you need to enter in a few items on this page:\

   1. Hostname (the base URL for your ControlShift account)\
      ​​
   2. REST API Application ID (Copy and paste this from the REST application page you have open in your browser)\
      ​
   3. REST API Application Secret (Copy and paste this from the REST application page you have open in your browser. \

4. Click "Save" to activate the integration.

Now go to the Pathways section in Daisychain and scroll down to Pathway Templates. Create a Pathway using the "ControlShift Petitions" template. A few things to know about your new Pathway:

* It has a set of default stages that you're welcome to edit.
* It comes with the "ControlShift Power-Up" activated, which enables it to display ControlShift integration.
* It automatically creates an Automation, which you can edit in Step 5 (See below).&#x20;

5. Go to Settings > Automations and review/edit the new automation that was just created.

That's it! We know there's a lot of steps here, and are standing by if we can help you setup this integration.
