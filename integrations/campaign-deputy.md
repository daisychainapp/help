---
description: How to set up and use the Daisychain / Campaign Deputy integration.
icon: user-tie
---

# Campaign Deputy

<figure><img src="../.gitbook/assets/integration-logos/campaign-deputy.png" alt="Campaign Deputy logo" width="36"><figcaption></figcaption></figure>

### Overview

The Campaign Deputy integration imports the people and contributions in your Campaign Deputy account into Daisychain and keeps them up to date. Once connected, you can text, filter, and run automations on your Campaign Deputy supporters without any CSV exports.

### Setup

To connect Campaign Deputy to Daisychain:

1. In Campaign Deputy, create an API token in your account settings. The token needs permission to read people.
2. In Daisychain, go to `Settings > Integrations > Campaign Deputy`.
3. Paste your API token and save.

Daisychain checks the token when you save it. If it's rejected, double-check that you copied the whole token and that it has permission to read people.

### What Gets Imported

**People**

Daisychain imports each person's name, primary email, primary phone, and primary address. Imported people are matched against people already in your account, so someone who is already in Daisychain won't be duplicated. Each person keeps their Campaign Deputy ID, which you can see on their profile.

**Contributions**

Contributions are imported once the first people import has finished. By default, Daisychain imports these contribution types:

* Check
* Cash
* In-kind
* Transfer
* Ticket purchase

Credit card contributions, and contributions processed by an online vendor such as ActBlue, are not imported from Campaign Deputy. If you use ActBlue, connect the [ActBlue integration](actblue.md) directly so those donations come in with full detail.

Imported contributions appear on the person's **Donations** tab alongside any ActBlue and FundraiseUp donations, and in their Timeline as "Donated $X via Campaign Deputy".

### Syncing

The first import runs as soon as you connect and can take a while for large accounts. You can follow its progress on `Settings > Integrations > Campaign Deputy`, which shows the sync status, when the last sync ran, and how many people have been imported.

After that, Daisychain pulls new and updated people and contributions from Campaign Deputy every hour. To pull the latest data right away, click **Sync Now**.

### Filtering

You can find people by their Campaign Deputy contributions using the **Activity** [filter](../managing-data/filtering-people.md) and choosing **Campaign Deputy Contribution**.

### Automation Triggers

You can trigger [automations](../organizing/automations/) when a contribution is recorded in Campaign Deputy. This makes it easy to thank donors or follow up with them.

Automations only run for contributions that are new to Daisychain. Contributions that were already imported before you created the automation won't trigger it.

### Troubleshooting

**The integration says it has been disabled**

If your API token stops working (for example, if it was deleted or expired in Campaign Deputy), Daisychain disables the integration and stops syncing. To fix it, create a new API token in Campaign Deputy, then go to `Settings > Integrations > Campaign Deputy`, enter the new token, and re-enable the integration.

**Removing the integration**

To disconnect Campaign Deputy, go to `Settings > Integrations > Campaign Deputy` and click **Remove Integration**. People already imported stay in your account, and past contributions stay in their Timeline. Their Campaign Deputy IDs, the contributions on their **Donations** tab, and any automations triggered by Campaign Deputy contributions are removed.
