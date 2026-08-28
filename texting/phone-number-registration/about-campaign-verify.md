---
description: Special instructions for political campaigns, party committees, and PACs
icon: message-check
---

# About "Campaign Verify"

If your organization is a political campaign, party committee, or PAC, you are required to register with "[Campaign Verify](https://www.campaignverify.org/)" before Daisychain can register your phone number. The carriers are moving toward requiring Campaign Verify for every political organization eligible for it.

Campaign Verify is only available to 527 organizations registered with the FEC or a state, local, or tribal election authority. If you're a 501(c)(3) or 501(c)(4), you can't get a token — see [below](#who-is-eligible-for-campaign-verify).

### **What's Campaign Verify?**

"Campaign Verify" is a third-party vetting provider for "[The Campaign Registry](https://www.campaignregistry.com/)", the organization that manages phone number registrations. These are both third-party organizations Daisychain works with to ensure your messages get delivered.

The verification process costs $95 and provides access to a token that authenticates your organization's identity and unlocks high-volume texting capacity on 10DLC.

### Who is eligible for Campaign Verify?

Any candidate, party, PAC, or other political committee that is a **527 tax-exempt organization** and is **registered with the Federal Election Commission (FEC) or a State, Local, or Tribal election authority** is eligible to obtain verification through Campaign Verify. Both parts matter: verification works by matching you to your public filing with that election authority. This includes:

* Federal candidate committees
* State, local, and tribal candidate committees
* Party committees at any level
* PACs
* Ballot initiative committees organized as 527s

**If you're eligible, Campaign Verify is required.** The carriers are increasingly requiring verification for political organizations that qualify for it — so Daisychain registers every eligible organization with the Political use case, and we can't complete your phone number registration without a token.

### Who can NOT get Campaign Verify?

{% hint style="warning" %}
**Campaign Verify is not available to 501(c)(3) or 501(c)(4) organizations.** This is true even for a c4 that sends explicitly political messages — eligibility depends on being a 527 registered with an election authority, not on the content of your messages. Campaign Verify will not issue a token to a c3 or c4, and it isn't something Daisychain can request on your behalf.

If you're a c3 or c4 and need more 10DLC throughput, your options are a Trust Score appeal or secondary vetting, or a toll-free number, which has no T-Mobile daily cap. See [Options if You're Hitting Message Limits](./#options-if-youre-hitting-message-limits), or email [help@daisychain.app,](mailto:help@daisychain.app) and we'll help you work out which makes sense.
{% endhint %}

Businesses and other non-political entities are also outside Campaign Verify's scope.

### What if my organization has both a 527 and a c3/c4 arm?

Only the 527 can be verified, and the token belongs to that entity. Your Daisychain account sends under a single telecom identity, so if that identity is your PAC, your sends use the PAC's Campaign Verify token regardless of which arm is paying for a given campaign. No regulator checks this message by message, but the telecom industry's preference is for the sending identity to match the entity actually sending. If you're not sure which entity your account is registered under, email [help@daisychain.app](mailto:help@daisychain.app) and we'll tell you what's on file.

### Why is it required?

Campaign Verify is how the telecom industry confirms a political sender is who it says it is, and it's the gateway to the Political use case. Without it, a 527's throughput is capped by its Trust Score like any other organization — as low as 2,000 messages per day to T-Mobile. With Campaign Verify and the Political use case, T-Mobile throughput is uncapped. It's increasingly required upstream by The Campaign Registry and the carriers, and it's the faster path, so we register every eligible organization this way.

### **How do I register with Campaign Verify?**

To register with Campaign Verify, follow the steps below:<br>

1. **Submit Verification Request**\
   To obtain a Campaign Verify token, fill out [the form on the Campaign Verify website](https://www.campaignverify.org/get-started) and follow their instructions. Please note there is a $95 verification fee. Once submitted, Campaign Verify will approve or reject your request, on a timeline that varies from just a few minutes to two business days.\
   ​
2. **Receive a PIN**\
   Following approval, Campaign Verify will provide you with a six-digit PIN code. This code is vital to generate your token, which allows unlimited texting capacity on 10DLC. Your method of receiving the PIN depends on the information in your public filing record.\
   ​
3. **Generate a Token**\
   Upon receiving your PIN code, log into your Campaign Verify account at [**Campaign Verify**](https://app.campaignverify.org/). Click on the name of your verified campaign, input your PIN at the bottom of the page, select "The Campaign Registry" as the service, and generate your token.\
   ​
4. **Share the Token with Daisychain**\
   Lastly, email your token to Daisychain, and we'll let you know when you're good to go!

{% hint style="info" %}
**Already have a Campaign Verify account and need to generate a new token to use with Daisychain?** When you create a 10DLC brand with Daisychain, you will need to provide a new Campaign Verify token, distinct from any previous tokens you’ve used. The process for creating a new token for an election cycle you have already been vetted to send messages for is quick and free.

To create a new token, please login to Campaign Verify, and scroll to the bottom of the page. There you will find a button to Create an Authorization Token. Please click this button to create the new token. The new token will be displayed underneath your existing tokens.&#x20;

_Some users may need to enroll in Multi Factor Authentication with Campaign Verify to complete this step._
{% endhint %}
