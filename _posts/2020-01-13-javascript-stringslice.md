---
image: "/assets/default-social-image.png"
title: JavaScript string.slice()
categories: JavaScript-strings
---

The.slice() method is a built-in javascript function used to return a section of the input string.

**Syntax:**

`string.slice(startingindex, endingindex)`

**Parameter:**

This function uses two startingindex and endingindex parameters (from/before which index, strings are to be started/included), respectively.

**Return Values:**

Returns a section or part of the input string specified.

Code #1:

```
<script>                     
   
   // Taking a string as input. 
   var A = 'Ram is going to school'; 
     
   // Calling of slice() function. 
   b = A.slice(0, 5); 
  
   // Here starting index is 1 given 
   // and ending index is not given to it so 
   // it takes to the end of the string   
   c = A.slice(1); 
     
   // Here endingindex is -1 i.e, second last character 
   // of the given string. 
   d = A.slice(3, -1); 
   e = A.slice(6); 
   document.write(b +"<br>"); 
   document.write(c +"<br>"); 
   document.write(d +"<br>"); 
   document.write(e);     
     
</script> 
```

Output:

```
Ram i
am is going to school
is going to schoo
going to school
```