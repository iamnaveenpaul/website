---
image: "/assets/default-social-image.png"
title: JavaScript String concat()
categories: JavaScript-strings
---

JavaScript uses the str.concat() function to join two or more strings together.

**Syntax:**

`str.concat(string2, string3, string4,......, stringN)`

**Arguments**

The arguments for this method are the strings to link together. For this function, the number of arguments is equivalent to the number of strings to be connected together.

**Return value**

This function returns a new string which is the combination as argument of all the different strings passed to it.

Example 1:

`print('It'.concat(' is',' a',' great',' day.'));`

Output:

`It is a great day.`

In this example, the concat() function combines “It” with ” is”, ” a”, ” great”, “day.” to create a final string with all the strings.

Program 1:

```
<script> 
// JavaScript to illustrate concat() function 
function func() { 
  
    // Original string 
    var str = 'It'; 
  
    // Joining the strings together 
    var value = str.concat(' is',' a',' great',' day.'); 
    document.write(value);     
} 
func(); 
</script>  
```

Output:

`It is a great day.`