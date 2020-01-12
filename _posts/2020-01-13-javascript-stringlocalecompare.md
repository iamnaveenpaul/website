---
image: "/assets/default-social-image.png"
title: JavaScript string.localeCompare()
categories: JavaScript-strings
---

The string.localCompare() is a JavaScript built-in function used to compare two elements and returns a positive number when the reference string is lexicographically larger than the comparison string or a negative number if the reference string is lexicographically lesser than the comparison string and zero (0), if reference and compare strings are equal.

Syntax:

`referenceString.localeCompare(compareString)`

**Parameters:**

Here the compareString parameter is a string associated with the reference string.

**Return Values:**

A positive number is reported if the reference string is more lexicographically than the comparison string and if the reference string is less lexicographically than the comparison string for negative number and zero (0) if the compare and the reference strings are similar.

Code #1:

```
<script> 
  
    // An alphabet "n" comes before "z" which 
    // gives a negative value 
    a = 'n'.localeCompare('z'); 
    document.write(a + '<br>') 
  
    // Alphabetically the word "gfc" comes after 
    // "grivaforgeeks" which gives a positive value 
    b = 'gfc'.localeCompare('grivaforgeeks'); 
    document.write(b + '<br>') 
  
    // "gfc" and "gfc" are equivalent which 
    // gives a value of zero(0) 
    c = 'a'.localeCompare('a'); 
    document.write(c) 
  
</script> 
```

Output:

```
-1
1
0
```

Code #2:

Also this function is for sorting elements.

```
<script> 
  
    // Taking some elements to sort alphabetically 
    var elements = [ 'gfc', 'grivaforgeeks', 'cse', 'department' ]; 
    a = elements.sort((a, b) => a.localeCompare(b)); 
  
    // Returning sorted elements 
    document.write(a) 
  
</script> 
```

Output:

`cse, department, grivaforgeeks, gfc`