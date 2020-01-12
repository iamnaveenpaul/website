---
image: "/assets/default-social-image.png"
title: JavaScript String.fromCharCode()
categories: JavaScript-strings
---

The function String.fromCharCode() is used to create a string of UTF-16 code units from the given sequence.

**Syntax:**

`String.fromCharCode(n1, n2, ..., nX)`

**Arguments**

The function takes as its argument the UTF-16 Unicode Sequences. The number of arguments relating to this function depends on the number of characters to join as a string. The number range lies between 0 and 65535.

**Return value**

This function's return value is a string comprising the characters whose UTF-16 codes have been passed as arguments to the function.

Example 1:

`print(String.fromCharCode(65, 66, 67));  `

Output:

`ABC`

In this example, the fromCharCode() function converts the UTF-16 codes into their equivalent characters, and returns the string that contains them as the answer. The answer to that is ABC in this case.

Example 2:

`String.fromCharCode(0x12014);`

Output:

`—`

In this case, the CharCode() function transforms the UTF-16 code into its corresponding character, and recovers the string that contains it as the answer. The answer in this case is —.

Program 1:

```
<script> 
// JavaScript to illustrate fromCharCode() function 
function func() { 
  
    // UTF-16 codes to be converted into characters 
    var str = String.fromCharCode(65, 66, 67); 
    document.write(str); 
} 
  
func(); 
</script> 
```

Output:

`ABC`

Program 2:

```
<script> 
// JavaScript to illustrate fromCharCode() function 
function func() { 
  
    // UTF-16 code to be converted into character 
    var str = String.fromCharCode(0x12014); 
    document.write(str);  
} 
  
func(); 
</script> 
```

Output:

`—`