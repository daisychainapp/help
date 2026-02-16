---
description: >-
  Daisychain's integration with the DNC's iwillvote.com lets you easily insert
  polling place information for US elections into your messages.
icon: check-to-slot
---

# Inserting Polling Place Info

{% hint style="warning" %}
This integration will only work if two conditions are met:&#x20;

**1) Polling place information needs to be available on the DNC's iwillvote.com website.** The DNC aims offer comprehensive coverage for major elections.&#x20;

**2) The people you are texting have ZIP codes.** Without zip codes, the polling place lookup will not work.&#x20;
{% endhint %}

### Overview

To send out polling information, you can use [variables](./) when composing your message in Step 2 of the [Campaign Creation](../campaigns/) process.

You can see key variables that are most commonly used are:

* **Polling Place Name:** `{{ person.primary_address.dnc_will_vote.locate.polling_locations[0].location_name }}`
* **Polling Place Address:** `{{ person.primary_address.dnc_will_vote.locate.polling_locations[0].location_name }}`
* **Polling Place Hours:** `{{ person.primary_address.dnc_will_vote.locate.polling_locations[0].dates_hours }}`.

To put it all together, below are few example messages that include variables.

### Sample Messages

**Sample Message - Election Day**

```
Hey {{ person.first_name }}, 📅 Election Day is Tuesday, November 3rd.  
  
{% if person.primary_address.dnc_will_vote and person.primary_address.dnc_will_vote.locate %}  

Here's all the info you need to vote in {{ person.primary_address.locality }}:  
  
🗳️ Your polling place is {{ person.primary_address.dnc_will_vote.locate.polling_locations[0].location_name }}.  
  
📍 Address: {{ person.primary_address.dnc_will_vote.locate.polling_locations[0].address_line_1 }}, {{ person.primary_address.dnc_will_vote.locate.polling_locations[0].city }}, {{ person.primary_address.dnc_will_vote.locate.polling_locations[0].state_code }} {{ person.primary_address.dnc_will_vote.locate.polling_locations[0].zip }}  
  
🕒 Polls are open from {{ person.primary_address.dnc_will_vote.locate.polling_locations[0].dates_hours }}.  
  
{% else %}  
  
🗳️ Please check your polling location at https://iwillvote.com.  
{% endif %}

```

Using the code above will output a message that looks something like this:

![](https://44727351.fs1.hubspotusercontent-na1.net/hubfs/44727351/image-png-4.png)

### **Sample Message - Early Vote**

```
Hey {{ person.first_name }}, Election Day is Tuesday, November 3rd, but you might be able to vote early!
{% if person.primary_address.dnc_will_vote and person.primary_address.dnc_will_vote.locate %}
Based on our records, here's all the info you need for early voting in {{ person.primary_address.locality }}:

🗳️ Your early voting location is {{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].location_name }}.

📍 Address: {{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].address_line_1 }}, {{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].city }}, {{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].state_code }} {{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].zip }}

🕒 Early voting hours: {{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].dates_hours }}.

🗳️ Please double-check to confirm your voting info here: https://iwillvote.com
{% else %}
🗳️ You can get all the info you need to vote here: https://iwillvote.com.
{% endif %}
```

Using the code above will output a message that looks something like this:

![](https://44727351.fs1.hubspotusercontent-na1.net/hubfs/44727351/image-png-Oct-14-2024-09-29-10-7274-PM.png)

**A note on data availability:** Data is available for major elections via the iWillVote API, but in some states polling place information isn't available until closer to the election. Additionally, some states don't have early voting and/or vote-by-mail at all.

**Accurate Addresses Needed:** We can't send out accurate polling place information to people in your Daisychain account unless they have accurate addresses. If the address information is missing, malformed, or inaccurate, they can't be geocoded, and Daisychain won't be able to determine their polling place.

### Full List of Daisychain Variables Using Info From iwillvote.com

| **Daisychain Variable**                                                                             | **Description**                                                                       |
| --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `{{ person.primary_address.dnc_will_vote.locate.polling_locations[0].location_name }}`              | Name of the **Election Day** polling place.                                           |
| `{{ person.primary_address.dnc_will_vote.locate.polling_locations[0].address_line_1 }}`             | Street address of the **Election Day** polling place.                                 |
| `{{ person.primary_address.dnc_will_vote.locate.polling_locations[0].city }}`                       | City of the **Election Day** polling place.                                           |
| `{{ person.primary_address.dnc_will_vote.locate.polling_locations[0].state_code }}`                 | State abbreviation of the **Election Day** polling place.                             |
| `{{ person.primary_address.dnc_will_vote.locate.polling_locations[0].zip }}`                        | ZIP code of the **Election Day** polling place.                                       |
| `{{ person.primary_address.dnc_will_vote.locate.polling_locations[0].dates_hours }}`                | **Election Day** polling hours.                                                       |
| `{{ person.primary_address.dnc_will_vote.locate.polling_locations[0].location_notes }}`             | Special notes about the **Election Day** polling location.                            |
| **Early Voting Locations**                                                                          | **(Below are variables for early voting locations)**                                  |
| `{{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].location_name }}`           | Name of the **early voting location**.                                                |
| `{{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].address_line_1 }}`          | Street address of the **early voting location**.                                      |
| `{{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].city }}`                    | City of the **early voting location**.                                                |
| `{{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].state_code }}`              | State abbreviation of the **early voting location**.                                  |
| `{{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].zip }}`                     | ZIP code of the **early voting location**.                                            |
| `{{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].dates_hours }}`             | Early voting **hours and dates** (e.g., “8:30 AM - 4:30 PM, Oct 15 - Nov 6”).         |
| `{{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].location_notes }}`          | Special notes about the **early voting location** (e.g., "Park behind the building"). |
| `{{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].schedule_exceptions }}`     | Exceptions to the schedule (e.g., "Closed on Sundays").                               |
| `{{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].schedule[0].date }}`        | First date this early voting location is open.                                        |
| `{{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].schedule[0].time_ranges }}` | Open and close times for a specific early voting date.                                |
| `{{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].schedule[0].is_open }}`     | Boolean (`true`/`false`): Is this early voting location open on this date?            |
| `{{ person.primary_address.dnc_will_vote.locate.early_vote_locations[0].schedule[0].is_24h }}`      | Boolean (`true`/`false`): Is this early voting location open **24 hours**?            |
| **Ballot Drop-Off Locations**                                                                       | **(Below are variables for drop-off locations)**                                      |
| `{{ person.primary_address.dnc_will_vote.locate.drop_off_locations[0].location_name }}`             | Name of the **ballot drop-off location**.                                             |
| `{{ person.primary_address.dnc_will_vote.locate.drop_off_locations[0].address_line_1 }}`            | Street address of the **ballot drop-off location**.                                   |
| `{{ person.primary_address.dnc_will_vote.locate.drop_off_locations[0].city }}`                      | City of the **ballot drop-off location**.                                             |
| `{{ person.primary_address.dnc_will_vote.locate.drop_off_locations[0].state_code }}`                | State abbreviation of the **ballot drop-off location**.                               |
| `{{ person.primary_address.dnc_will_vote.locate.drop_off_locations[0].zip }}`                       | ZIP code of the **ballot drop-off location**.                                         |
| `{{ person.primary_address.dnc_will_vote.locate.drop_off_locations[0].dates_hours }}`               | Ballot drop-off **hours and dates** (e.g., “24/7 from Oct 15 - Nov 6”).               |
| `{{ person.primary_address.dnc_will_vote.locate.drop_off_locations[0].schedule_exceptions }}`       | Exceptions to the drop-off schedule (e.g., "Closed on Sundays").                      |
| `{{ person.primary_address.dnc_will_vote.locate.drop_off_locations[0].open_early_voting }}`         | Boolean (`true`/`false`): Is this location open **during early voting**?              |
| `{{ person.primary_address.dnc_will_vote.locate.drop_off_locations[0].open_election_day }}`         | Boolean (`true`/`false`): Is this location open **on Election Day**?                  |
