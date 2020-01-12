---
image: "/assets/default-social-image.png"
title: JavaScript String split()
categories: JavaScript-strings
---

The str.split() method is used to separate the defined string into a string array by splitting it into a substring using a specified separator provided in the argument.

**Syntax:**

`str.split(separator, limit)`

**Arguments**

The first argument to this method is a string specifying the points where the split is to occur. You can treat this argument as a simple string or as a regular expression. If the separator is unspecified then the whole string will become one array element. The same occurs when there is no separator present in the string. If the separator is an empty string (“”) , then each string character is split.

The second argument to the function limit determines the upper limit on the number of splits in the specified string to be identified. If after hitting the limit the string stays unchecked, then it is not stated in the array.

**Return value**

This method returns an array of strings that is generated at every point where the separator occurs after separating the specified string.

Example 1:

```
var str = 'It iS a 5r&e@@t Day.'
var array = str.split(" ");
print(array);
```

Output:

`[It,iS,a,5r&e@@t,Day.]`

In this case, the split() method generates a string array by splitting str anywhere " " happens.

Example 2:

```
var str = 'It iS a 5r&e@@t Day.'
var array = str.split(" ",2);
print(array);
```

Output:

`[It,iS]`

In this case, the split() method generates a string array by splitting str everywhere "" happens. The second argument 2 limits the number of such splits to just 2.

Program 1:

```
<script> 
// JavaScript Program to illustrate split() function 
  
function func() { 
    //Original string 
    var str = 'It iS a 5r&e@@t Day.'
    var array = str.split(" "); 
    document.write(array);   
} 
  
func(); 
</script> 
```

Output:

`[It,iS,a,5r&e@@t,Day.]`

Program 2:

```
<script> 
// JavaScript Program to illustrate split() function 
  
function func() { 
  
    // Original string 
    var str = 'It iS a 5r&e@@t Day.'
  
    // Splitting up to 2 terms 
    var array = str.split(" ",2); 
    document.write(array);  
} 
  
func(); 
</script> 
```

Output:

`[It,iS]`