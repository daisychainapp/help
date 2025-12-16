---
icon: rectangle-code
---

# Charms Coding Tips

_The most important thing to know about writing code for a Charm is that it uses a very specific subset of HTML and CSS._

One of the main differences between standard CSS and the subset supported by Charms is that Charms only supports `display:flex`&#x20;

Inline and block display modes that you might be used to as the default display modes in typical web development probably won’t work like you expect them.

This makes some things easier and others harder — centering text vertically within your image is very easy, something that `display:block` struggles with, for example.&#x20;

One thing that’s a little more complicated than usual is styling specific words within text. A element within a flexbox might not behave the way you expect it to if you’re used to inline elements, especially when it comes to wrapping text around a new line.

If you’re trying to style individual words within a line of text, we recommend using CSS to make the flexbox behave as close to an inline container as possible by:

* Wrapping each paragraph in a `div` styled with `display:flex`, `flex-direction:row,` and `flex-wrap:wrap`
* Wrapping each word in the paragraph in a tag (yes, it's a little annoying) and using margin to replicate the proper spacing between words.

Here’s some CSS to do this:

```
.inline-container{  
  
display: flex;  
  
flex-direction: row;  
  
flex-wrap: wrap;  
  
width:100%;  
  
}  
  
.inline-container span{  
  
margin-right:8px;  
  
}
```

&#x20;
