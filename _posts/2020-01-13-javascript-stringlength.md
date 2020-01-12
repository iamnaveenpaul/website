---
image: "/assets/default-social-image.png"
title: JavaScript string.length
categories: JavaScript-strings
---

The string.length is a JavaScript property that is used to find a certain string's length.

**Syntax:**

`string.length`

**Parameter:**

No parameter is acceptable.

**Return Values:**

The length of the specified string is returned.

Code #1:

```
<script> 
  
    // Taking some strings 
    var x = 'grivaforgeeks'; 
    var y = 'gfg'; 
    var z = ''; 
  
    // Returning the length of the string. 
    document.write(x.length + "<br>"); 
    document.write(y.length + "<br>"); 
    document.write(z.length); 
  
</script> 
```

Output:

```
13
3
0
```

Code #2:

```
<script> 
  
    // Taking some strings. 
    var x = '2341312134'; 
    var y = '@#$%^&**((*&^'; 
  
    // Variable z contains two spaces 
    var z = '  '; 
  
    // Returning the length of the string. 
    document.write(x.length + "<br>"); 
    document.write(y.length + "<br>"); 
    document.write(z.length); 
  
</script> 
```

Output:

```
10
13
2
```