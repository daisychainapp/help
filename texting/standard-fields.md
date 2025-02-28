---
icon: input-text
---

# Standard Fields

_When you import a CSV into Daisychain, you should include column headers for each field._

Standard headers found in the template file (available [here](https://go.daisychain.app/uploads/people.csv) and in Step One of the [CSV Import Wizard](https://help.daisychain.app/daisychain-csv-imports)). Alternative header names will be auto-matched by our importer -- see the table a the bottom of this help doc for more details.&#x20;

Note that you do not need to include _all_ of the fields below when uploading a CSV file -- the minimal requirement for successful CSV upload is email address and/or phone number.&#x20;

*

**first\_name**\
​

*

**last\_name**\
​

*

**email**\
​

*

**phone\_number**\
​

*

**email\_opt\_in**\
Values for this field must be "TRUE" to ensure a person can receive emails through Daisychain.\
​

*

**sms\_opt\_in**\
Values for this field must be "TRUE" to ensure a person can receive text messages through Daisychain.\
​

*

**sms\_opt\_out**\
If values for this field are "TRUE", the person will be marked as unsubscribed for text messages through Daisychain.\
​

*

**post\_office\_box**\
​

*

**street\_address**\
​

*

**extended\_address**\
Often known as "line two" of an address.\
​

*

**locality**\
Town or city\
​

*

**region**\
State, province, or region. Values for this field should be two or three letters, following the [ISO 3166 standard](https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes). In the United States, use the two letter abbreviation for the state.\
​

*

**postal\_code**\
Also known as a ZIP code or post code.\
​

*

**country**\
Values for this field should be two letters. If you're unsure of the right two-letter country code, please reference the [List of ISO 3166 country codes](https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes), and look for the Alpha-2 column.\
​

*

**tags**\
Values for this field should be lowercase and without any spaces -- any spaces in tags should be replaced by dashes. Multiple tags can included in a single column, separated by commas. [Tags need to first be created in Daisychain](https://help.daisychain.app/tags) before they can be added with a CSV upload.

### Full list of accepted header names

\| **Field Name** | **Accepted Inputs** | | First Name | first\_name, firstname, FirstName, First Name, first name, fname, FName, First | | Last Name | last\_name, lastname, LastName, Last Name, last name, lname, LName, Last | | Email | email, Email, email\_address, emailaddress, EmailAddress, email address, Email Address | | Phone Number | phone\_number, phonenumber, PhoneNumber, phone number, Phone Number, phone, Phone, Cell Phone, cell\_phone, cellphone, CellPhone, cell phone, mobile, Mobile, Mobile Phone, mobile\_phone, mobilephone, MobilePhone, mobile phone | | Email Opt-In | email\_opt\_in, emailoptin, EmailOptIn, email opt in | | Email Opt-Out | email\_opt\_out, emailoptout, EmailOptOut, email opt out | | SMS Opt-In | sms\_opt\_in, smsoptin, SmsOptIn, sms opt in | | SMS Opt-Out | sms\_opt\_out, smsoptout, SmsOptOut, sms opt out | | Post Office Box | post\_office\_box, postofficebox, PostOfficeBox, post office box | | Street Address | street\_address, streetaddress, StreetAddress, street address, Street Address, address, Address | | Postal Code | postal\_code, postalcode, PostalCode, postal code, zip\_code, zipcode, ZipCode, zip code, Zip Code, Zip, zip | | Extended Address | extended\_address, extendedaddress, ExtendedAddress, extended address | | City | locality, Locality, City, Town, city, town | | State/Region | region, Region, State, state, province, Province | | Country | country, Country | | Tags | tags, Tags, tag, Tag |
