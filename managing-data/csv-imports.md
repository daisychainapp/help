---
description: You can easily add people to your Daisychain through CSV uploads.
icon: file-csv
---

# CSV Imports

{% embed url="https://www.loom.com/share/ea6ff12528e747c09fee849cfae70da3?sid=4bb34e37-38d9-48b5-bea6-9e2f4374edc9" %}



Importing people into Daisychain is simple:

* First, navigate to the "People" section of Daisychain.
* Then, click the button with three dots and click "Import CSV":

<figure><img src="../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

You'll then be guided through the four step upload process:

1. **Upload.** In this step, you'll either drag-and-drop your CSV file onto the upload area, or you can click it to select the file from a folder on your computer. Note that Daisychain only accepts CSV files (not Excel files).&#x20;

{% hint style="success" %}
CSV files can include data for both [Standard Fields](standard-fields.md) and [Custom Fields](custom-fields.md) — but if you're importing data to Custom Fields, you'll want to create those fields before importing your CSV. Additionally, CSVs must include values for email and/or phone number for every person that you're importing into Daisychain.&#x20;
{% endhint %}

{% hint style="info" %}
If you'd like to apply [Tags](tags.md) to the people you're importing via CSV, tags must first be created. Values for this field should be lowercase and without any spaces — any spaces in tags should be replaced by dashes. So a "Super Volunteer" tag would get imported as "super-volunteer." Multiple tags can included in a single column, separated by commas.&#x20;
{% endhint %}

2. **Map Fields.** This step is where you can look at how your fields are being mapped and identify any problems before proceeding to the actual Import step. You can adjust how fields are mapped on this step as well.<br>
3. **Settings:** Decide how Daisychain handles existing contacts based on phone and email matching. If Daisychain finds matching records in your CSV that correspond to existing People in your Daisychain account (records that have identical phone number or email address as the people you're uploading) you can choose how to handle the new data:
   1. Merge new data only: Adds new fields without changing existing data.
   2. Overwrite existing data: Replaces current data with imported values.<br>
4. **Import.** On this stage you'll monitor the progress of your import, which includes two distinct phases importing the data and rebuilding the audiences. You'll also be able to view and export errors from your import.&#x20;

After your import is complete, you can press "Continue" to take quick actions like adding the people you imported to a [Pathway](../organizing/pathways.md) or targeting them in a [Campaign](../texting/campaigns/).

{% hint style="warning" %}
If any of rows in your CSV contain cells with invalid values (i.e. malformed email addresses, non-existent postal codes, etc.) Daisychain will reject the entire row so that you can fix the errors and re-upload those people with valid data. Any valid rows in that CSV will be processed and imported normally.&#x20;
{% endhint %}
