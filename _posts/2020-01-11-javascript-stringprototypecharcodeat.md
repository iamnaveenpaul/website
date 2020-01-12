---
image: "/assets/default-social-image.png"
title: JavaScript String.prototype.charCodeAt()
categories: JavaScript-strings
---

The function str.charCodeAt() returns the Unicode character set code unit of the character contained in the string stated as the argument.

**Syntax:**

`str.charCodeAt(index)`

**Arguments**

The only argument to this function is the character index in the string which is to use Unicode. The index range is from 0 till length -1.

**Return value**

This function returns the Unicode (ranging from 0 to 65535) of the character whose index is supplied as argument to the function. If the index given is out of range, it returns NaN for this function.

Example 1:

```
Input:
var str = 'ephemeral';
print(str.charCodeAt(4));
```

Output:

`109`

In this example the charCodeAt() function extracts the string character at index 4. This function returns the Unicode sequence as 109 because this character is m.

Example 2:

```
Input:
var str = 'ephemeral';
print(str.charCodeAt(20));
```

Output:

`NaN`

In this case, the charCodeAt() function extracts the character at index 20 from the string. Because the index for the string is out of range, this method returns the result as NaN.

Program 1:

```
<script> 
// JavaScript to illustrate charCodeAt() function 
  
function func() { 
    var str = 'ephemeral'; 
  
    // Finding the code of the character at 
    // given index  
    var value = str.charCodeAt(4); 
    document.write(value);     
} 
  
func(); 
</script> 
```

Output:

`109`

Program 2:

```
<script> 
// JavaScript to illustrate charCodeAt() function 
  
function func() { 
    var str = 'ephemeral'; 
  
    // Finding the code of the character  
    // at given index  
    var value = str.charCodeAt(20); 
  
    document.write(value);     
} 
func(); 
</script>  
```

Output:

`NaN`