---
description: >-
  Daisychain allows you to customize your text messages with personalized and
  dynamic content.
icon: brackets-curly
---

# Personalized Content

Daisychain uses Shopify’s “Liquid” framework to power "variables", which allows for advanced personalization. Variables can be identified by being inside curly brackets, like this:\
\
`{{ example_variable }}`

In addition to the tips in this article, you can read more about Liquid with [this cheat sheet](https://www.shopify.com/partners/shopify-cheat-sheet).

### **Inserting variables**

You can insert variables into messages by clicking the curly braces under the message you are crafting.

You have quick access to the most commonly used variable (First Name), and can access other variables by expanding the three menus ("Account", "Person", and "User"):

![](https://44727351.fs1.hubspotusercontent-na1.net/hubfs/44727351/image-png-3.png)

The general format is:

`{{ person.dynamic_field }}`

#### **IF Statements**

Daisychain allows you to customize dynamic fields using IF statements. The general format is:

`{% if STATEMENT %}`

`{% else %}`

`{% endif %}`

For example, if you would like to display a certain message based on a voter’s sweet treat preference, you could use the following formatting (referencing the “Sweet Treat” custom field):

{% code overflow="wrap" %}
```liquid
Hey {{ person.first_name }}! 
{% raw %}
{% if person.sweet_treat_preference == "Honey" %}  
Win a trip to eat honey with Christopher Robin!  
{% else %}    
You can win a trip to see Christopher Robin! 
{% endif %}
{% endraw %} 
```
{% endcode %}

#### **Default values**

For most dynamic fields, you can include a default value by including:

```
| default:"default here"
```

For example, for first name defaulting to "Friend," you may use:

```
{{ person.first_name | default:"Friend" }}
```

If you are attempting to set a default value for a dynamic field with multiple layers (for example, state name within address), you will need to first check if the value exists, like so:

```liquid
{% raw %}
{% if person.primary_address and person.primary_address.region %}  
  
  {{ person.primary_address.region_data.name }}  
  
{% else %}  
  
   Your State  
  
{% endif %}
{% endraw %}
```

