---
image: "/assets/default-social-image.png"
title: JavaScript String substr()
categories: JavaScript-strings
---

The str.substr() function returns the defined number of characters from the given string index.

**Syntax:**

`str.substr(start , length)`

**Arguments:**

The first argument to the start function determines the starting index from which to remove the substring from the base string. The second argument on the length of the function determines the number of characters to be collected in the provided string from the beginning. If the second argument to the function is undefined then all characters are extracted from the beginning until the end of the length.

**Return value:**

This method returns a string which is part of the string provided. If the length is 0 or negative value then an empty string returns.

Example 1:

```
var str = 'It is a great day.'
print(str.substr(5));
```

Output:

` a great day.`

In this illustration, the substr() function produces a substring from index 5 until the end of the string.

Example 2:

```
var str = 'It is a great day.'
print(str.substr(5,6));
```

Output:

` a gre`

In this instance, the substr() function extracts the substring from index 5 and the string length is 6.

Example 3:

```
var str = 'It is a great day.'
print(str.substr(5,-7));
```

Output:

```

```

Therefore, in this instance, the function returns an empty string since the length of the string to be extracted is negative.

Program 1:

```
<script> 
// JavaScript to illustrate substr() function 
  
function func() { 
  
    // Original string 
    var str = 'It is a great day.'; 
    var sub_str = str.substr(5); 
    document.write(sub_str); 
} 
  
func(); 
</script> 
```

Output:

` a great day.`

Program 2:

```
<script> 
// JavaScript to illustrate substr() function 
  
function func() { 
  
    // Original string 
    var str = 'It is a great day.'; 
  
    var sub_str = str.substr(5,6); 
    document.write(sub_str); 
} 
  
func(); 
</script> 
```

Output:

` a gre`

Program 3:

```
<script> 
// JavaScript to illustrate substr() function 
  
function func() { 
  
    // Original string 
    var str = 'It is a great day.'; 
  
    var sub_str = str.substr(5,-7); 
    document.write(sub_str); 
} 
func(); 
</script> 
```

Output:

```

```