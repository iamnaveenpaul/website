---
image: "/assets/default-social-image.png"
title: JavaScript string.repeat()
categories: JavaScript-strings
---

The string.repeat() is a built-in function of JavaScript used for building a new string with the given number of copies in that string on calling this method.

Syntax:

`string.repeat(a);`

**Parameters:**

The parameter 'a' here is an integer value that shows the number of times the string is replicated. The scope is from zero (0) to infinity for the integer "a".

**Return values:**

The string returns the number of copies of a string specified.

Code #1:

```
<script> 
  
    // Taking a string "gfc" 
    A = "gfc"; 
  
    // Repeating the string multiple times 
    a = A.repeat(5); 
    document.write(a); 
  
</script> 
```

Output:

`gfcgfcgfcgfcgfc`

Code #2:

```
<script> 
  
    // Taking a string "gfc" 
    A = "gfc"; 
  
    // Repeating the string 2.9 times i.e, 2 times 
    // because 2.9 conterted into 2 
    b = A.repeat(2.9); 
    document.write(b + "<br>"); 
  
</script> 
```

Output:

`gfcgfc`