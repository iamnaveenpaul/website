---
image: "/assets/default-social-image.png"
title: JavaScript string.codePointAt()
categories: JavaScript-strings
---

The.codePointAt() string is an built-in method in JavaScript used to return a non-negative integer value, that is to say the code point value of the provided string element.

**Syntax:**

`string.codePointAt(A)`

**Parameters:**

It accepts a parameter that displays the index of the string element. Starting index is zero (0).

**Return Values:**

It returns the value of the element code point which is indicated in the string by parameter. It returns undefined if the specified position, i.e. the "A"th index has no element present.

Code #1:

```
<script> 
  
    // Taking a string "gfc" 
    a = "gfc"
  
    // Pointing each elements of the string 
    b = a.codePointAt(0); 
    c = a.codePointAt(1); 
    d = a.codePointAt(2); 
  
    // Printing the code point value of each element 
    document.write(b + "<br>") 
    document.write(c + "<br>") 
    document.write(d) 
  
</script> 
```

Output:

```
103
102
103
```

Code #2:

```
<script> 
  
    // Taking a string "gfc" 
    a = "gfc"
  
    // Pointing 4th index of the string 
    // index starts from 0 
    b = a.codePointAt(3); 
  
    // Printing the code point value 
    document.write(b + "<br>") 
  
</script> 
```

Output:

`undefined`

Note: Output is undefined because there's no 4th index element in "gfc".