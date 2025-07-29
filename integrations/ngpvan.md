---
description: >-
  The NGPVAN <> Daisychain integration allows you to import lists from VAN, NGP,
  Votebuilder, and EveryAction into your Daisychain People database.
icon: poll-people
---

# NGPVAN

### Overview and Setup

{% hint style="info" %}
**A note on names**\
This document refers to "NGPVAN" and "VAN", but the instructions also apply if you are importing lists from Bonterra products named VoteBuilder, EveryAction, and more. For information about integrating live form submissions from these products, [click here.](everyaction.md)
{% endhint %}

To setup this integration, you'll first need to request an API key from NGPVAN by clicking "Contact the Admin" on the Main Menu while logged into your NGPVAN account.

Once you have this API key and API application name, go to your Daisychain account and navigate to Settings → Integrations and click "Add" in the VAN CRM box:

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

You should then see this form:

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

Fill out this form using the VAN API key and application name provided by your VAN admin.

If you’d like to sync lists of your voters, select “My Voters” under “API Mode,” and if you’d like to sync lists of your campaign (or NGP lists), select “My Campaign”. Once added, click “save”.

### Selecting lists from VAN

All lists and folders in VAN which are shared with your API key will be visible in Daisychain. To ensure a list is visible to your API key, edit your folder and scroll down to “User Access,” you will see something like this:

<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

Select the Daisychain API user, and click “Add”. Verify that the access looks something like below and then click save:

<figure><img src="../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

Note: Lists which appear in multiple folders will cause errors in Daisychain; please ensure that each list is only in one unique folder.

### Importing lists from VAN

All folders you have shared with the Daisychain API will be listed under the “List” tab.

<figure><img src="../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

To import a list, click the arrow button by a folder:

<figure><img src="../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

Clicking “Import” will move the selected list into Daisychain. And once completed, you will see how many people were successfully imported.

<figure><img src="../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

To view errors, click the list name, and you will be taken to the import summary page. Here, you will see a list of import errors, and stats about your imported list.

<figure><img src="../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

**Import errors and notes**

* People without a phone number or without a valid phone number will not be imported into Daisychain
* Only the first phone number listed for people will import into Daisychain.

### Viewing and filtering VAN information

Once you have imported a list to Daisychain, information from VAN will appear on the people page in Daisychain.

<figure><img src="../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

You can select a VAN list to filter by, and on an individual person’s page you can see information about that person’s VAN ID:

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

### Syncing Opt-outs

Whenever you opt someone out in Daisychain, that information will sync back to VAN as an opt out as well. [Learn more about subscription statuses here.](../managing-data/subscription-statuses.md)
