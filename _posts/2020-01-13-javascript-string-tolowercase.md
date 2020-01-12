---
image: "/assets/default-social-image.png"
title: JavaScript String toLowerCase()
categories: JavaScript-strings
---

Str.toLowerCase() converts the entire string to a lower case. This function will not affect any of the special characters, digits or alphabets already in the lower case.

**Syntax:**

`str.toLowerCase()`

**Arguments**

This function takes up no arguments at all.

**Return value**

This function reverts a new string where all letters in the upper case are transformed to lower case.

Example 1:

```
var str = 'It iS a Great Day.';
var string = str.toLowerCase();
print(string);
```

Output:

`it is a great day.`

In this illustration, the toLowerCase() function converts all the alphabets of the upper case into alphabets of the lower case, without impacting the special characters, digits and all those characters already in the lower case.

Example 2:

```
var str = 'It iS a 5r&e@@t Day.';
var string = str.toLowerCase();
print(string);
```

Output:

`it is a 5r&e@@t day.`

In this example the toLowerCase() function converts all alphabets of the upper case into alphabets of the lower case without affecting the special characters, digits and all those characters that are already in the lower case.

Program 1:

```
<script> 
// JavaScript Program to illustrate 
//  toLowerCase() function 
  
function func() { 
     
    // Original string 
    var str = 'It iS a Great Day.'; 
     
    // Converting to lower case 
    var string = str.toLowerCase(); 
    document.write(string); 
} 
  
func(); 
</script> 
```

Output:

`it is a great day.`

Program 2:

```
<script> 
// JavaScript Program to illustrate 
//  toLowerCase() function 
  
function func() { 
     
    //Original string 
    var str = 'It iS a 5r&e@@t Day.'; 
     
    //Converting to lower case 
    var string = str.toLowerCase(); 
    document.write(string); 
} 
  
func(); 
</script> 
```

Output:

`it is a 5r&e@@t day.`