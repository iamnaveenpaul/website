---
image: "/assets/default-social-image.png"
title: JavaScript escape()
categories: JavaScript-functions
---

The escape() function takes and encodes a string as a parameter so that any network that supports ASCII characters can be transferred to any computer.

**Syntax :**

`escape(string)`

Note: Only special characters are encoded in this function.

Exceptions : @ – + . / * _

```
<script> 
  
// Special character encoded with 
// escape function 
document.write(escape("This is my World!!!")); 
  
document.write("<br>"); 
  
// Print encoded string using escape() function 
// Also include exceptions i.e. @ and . 
document.write(escape("To contribute articles contact us at" + 
                       "dozenalism@gmail.com")); 
</script> 
```

Output :

```
This%20is%20my%20World%21%21%21
To%20contribute%20articles%20contact%20us%20atdozenalism@gmail.com
```