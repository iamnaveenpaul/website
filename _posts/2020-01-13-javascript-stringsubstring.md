---
image: "/assets/default-social-image.png"
title: JavaScript string.substring()
categories: JavaScript-strings
---

The string.substring() method is an built-in JavaScript function that is used to return the section from the start index to the end index of this string. Starting with zero (0) indexing.

**Syntax:**

`string.substring(Startindex, Endindex)`

**Parameters:**

The Startindex and Endindex define here the section of the string for substring. Endindex is optional.

**Return value:**

It returns a new string that is included in the specified string.

Code #1:

```
<script> 
  
    // Taking a string as variable 
    var string = "grivaforgeeks"; 
    a = string.substring(0, 4) 
    b = string.substring(1, 6) 
    c = string.substring(5) 
    d = string.substring(0) 
  
    // Printing new string which are 
    // the part of the given string 
    document.write(a + "<br>"); 
    document.write(b + "<br>"); 
    document.write(c + "<br>"); 
    document.write(d + "<br>"); 
  
</script> 
```

Output:

```
griv
rivaf
forgeeks
grivaforgeeks
```

Code #2:

The index always starts at 0. If we still consider the index as negative, then the index is considered zero and the index can not be fractionated, and if it does, it will be converted into a whole number which is lesser in value than it.

```
<script> 
  
    // Taking a string as variable 
    var string = "grivaforgeeks"; 
    a = string.substring(-1) 
    b = string.substring(2.5) 
    c = string.substring(2.9) 
  
    // Printing new string which are 
    // the part of the given string 
    document.write(a + "<br>"); 
    document.write(b + "<br>"); 
    document.write(c + "<br>"); 
  
</script> 
```

Output:

```
grivaforgeeks
ivaforgeeks
ivaforgeeks
```