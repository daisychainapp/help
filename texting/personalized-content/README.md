---
description: >-
  Daisychain allows you to customize your text messages with personalized and
  dynamic content using variables.
icon: brackets-curly
---

# Personalized Content

Daisychain uses Shopify’s “Liquid” framework to power variables, which allows for complex personalization. In addition to the tips in this article, you can read more about Liquid with [this cheat sheet](https://www.shopify.com/partners/shopify-cheat-sheet).

### **Inserting dynamic content**

You can insert dynamic content into messages by clicking the curly braces under the message you are crafting.

You have quick access to the most commonly used variable (First Name), and can access other variables by expanding the three menus ("Account", "Person", and "User"):

![](https://44727351.fs1.hubspotusercontent-na1.net/hubfs/44727351/image-png-3.png)

The general format is:

```
{{ person.dynamic\_field }}
```

#### **IF Statements**

Daisychain allows you to customize dynamic fields using IF statements. The general format is:

`{% if STATEMENT %}`

`{% else %}`

`{% endif %}`

For example, if you would like to display a certain message based on a voter’s sweet treat preference, you could use the following formatting (referencing the “Sweet Treat” custom field):

Message:

```
Hey {{ person.first\_name }}! {% raw %}
{% if person.sweet\_treat\_preference == "Honey" %}  
  
Win a trip with all you can eat honey with Christopher Robin  
  
{% else %}  
  
You can win a trip to see Christopher Robin!  
  
{% endif %}
{% endraw %}  
  

```

#### **Default values**

For most dynamic fields, you can include a default value by including:

```
| default:"default here"
```

&#x20;

For example, for first name defaulting to "Friend," you may use:

```
{{ person.first\_name | default:"Friend" }}
```

If you are attempting to set a default value for a dynamic field with multiple layers (for example, state name within address), you will need to first check if the value exists, like so:

```
{% raw %}
{% if person.primary\_address and person.primary\_address.region %}  
  
  {{ person.primary\_address.region\_data.name }}  
  
{% else %}  
  
   Your State  
  
{% endif %}
{% endraw %}
```

&#x20;
