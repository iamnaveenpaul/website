---
image: "/assets/default-social-image.png"
title: JavaScript String toUpperCase()
categories: JavaScript-strings
---

Function str.toUpperCase() converts the whole string to Upper case. This function does not affect any of the special characters, digits or alphabets in the upper case already.

**Syntax:**

`str.toUpperCase()`

**Arguments**

This function takes up no arguments at all.

**Return value**

This function returns a new string which transforms all lower case letters into upper case.

Example 1:

```
var str = 'It iS a Great Day.';
var string = str.toUpperCase();
print(string);
```

Output:

`IT IS A GREAT DAY.`

In this illustration, the toUpperCase() method converts all the lower case alphabets to their upper case counterparts without impacting the special characters and the digits.

Example 2:

```
var str = 'It iS a 5r&e@@t Day.'
var string = str.toUpperCase();
print(string);
```

Output:

`IT IS A 5R&AMP;E@@T DAY.`

The method toUpperCase() in this illustration transforms all the lower case alphabets to their upper case counterparts without impacting the special characters and the digits.

Program 1:

```
<script> 
// JavaScript to illustrate .toUpperCase()  
  
function func() { 
      
    // Original string 
    var str = 'It iS a Great Day.'; 
      
    // String converted to Upper Case 
    var string = str.toUpperCase(); 
    document.write(string); 
} 
  
func(); 
</script> 
```

Output:

`IT IS A GREAT DAY.`

Program 2:

```
<script> 
// JavaScript to illustrate .toUpperCase()  
function func() { 
      
    //Original string 
    var str = 'It iS a 5r&:ampe@@t Day.'
      
    //String converted to Upper Case 
    var string = str.toUpperCase(); 
    document.write(string); 
} 
  
func(); 
</script> 
```

Output:

`IT IS A 5R&:AMPE@@T DAY.`