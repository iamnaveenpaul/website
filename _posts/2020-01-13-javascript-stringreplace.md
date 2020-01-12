---
image: "/assets/default-social-image.png"
title: JavaScript string.replace()
categories: JavaScript-strings
---

The string.replace() is a built-in function in JavaScript that replaces a portion of the specified string with some other string or a regular expression. The first string remains unchanged.

**Syntax:**

`str.replace(A, B)`

**Parameters:**

Parameter A is a regular expression and parameter B is a string to substitute the content of the string provided.

**Return Values:**

Returns a new string of things replaced.

Code #1:

In this scenario the GrivaForCoding string contents is substituted with gfc.

```
<script> 
  
    // Assigning a string 
    var string = 'GrivaForCoding is a CS portal'; 
  
// Calling replace() function 
var newstring = string.replace(/GrivaForCoding/, 'gfc'); 
  
// Printing replaced string 
document.write(newstring); 
  
</script> 
```

Output:

`gfc is a CS portal`

Code #2:

```
<script> 
  
    // Taking a regular expression 
    var re = /GrivaForCoding/; 
  
// Taking a string as input 
var string = 'GrivaForCoding is a CS portal'; 
  
// Calling replace() function to replace 
// GrivaForCoding from string with gfc 
var newstring = string.replace(re, 'gfc'); 
  
// Printing new string with replaced items 
document.write(newstring); 
  
</script> 
```

Output:

`gfc is a CS portal`