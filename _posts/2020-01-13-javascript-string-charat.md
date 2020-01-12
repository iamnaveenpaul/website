---
image: "/assets/default-social-image.png"
title: JavaScript String charAt()
categories: JavaScript-strings
---

The str.charAT() returns a string index character.

**Syntax:**

`character = str.charAt(index)`

**Arguments**

The only argument to this function is the index in the string from which to extract the single character. This index range is between 0 and length-1, including the limits. If no index is indicated then the string's first character is returned, since 0 is the default index used for this function.

**Return value**

This function returns a single character to the function located at the index specified as the argument. If the index is out of range then an empty string returns for this function.

Example 1:

```
var str = 'JavaScript is object oriented language';
print(str.charAt(9));
```

Output:

`t`

In this example the charAt() function finds the character and returns it at index 9.

Example 2:

```
var str = 'JavaScript is object oriented language';
print(str.charAt(50));
```

Output:

```

```

So since the index for the specified string is out of bounds the function generates "" an empty string.

Program 1:

```
// JavaScript to illustrate charAt() function 
<script> 
function func() { 
  
    // Original string 
    var str = 'JavaScript is object oriented language'; 
  
    // Finding the character at given index  
    var value = str.charAt(9); 
    document.write(value);   
} 
func(); 
</script>   
```

Output:

`t`

Program 2:

```
<script> 
// JavaScript to illustrate charAt() function 
function func() { 
  
    // Original string 
    var str = 'JavaScript is object oriented language'; 
  
    // Finding the character at given index  
    var value = str.charAt(50); 
    document.write(value);     
} 
func(); 
</script>   
```

Output:

```

```