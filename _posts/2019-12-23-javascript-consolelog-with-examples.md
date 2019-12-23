---
image: "/assets/default-social-image.png"
title: JavaScript console.log() with Examples
categories: JavaScript-function
---

The console.log() is a function of JavaScript that is used to display some predefined variables or just to print any message that needs to be displayed to the user.

**Syntax:**

`console.log(A);`

Parameters: A parameter that can be an array, an object or any message is accepted.

Return value: returns the value of the specified parameter.

Codes to show the working of this function:

**1) Passing a number as an argument:** If the number is passed to the console.log() function, it will be displayed by the function.

**Code #1:**

```
<script> 
var a = 2; 
console.log(a); 
</script> 
```

**2) Passing a string as an argument:** If the string is passed to console.log() function, it will be displayed by the function.

**Code #2:**

```
<script> 
var str = "This is my World"; 
console.log(str); 
</script> 
```

**3) Passing a char as an argument:** If the char is passed to console.log(), it will be displayed by the function.

**Code #3:**

```
<script> 
var ch = '2'; 
console.log(ch); 
</script> 
```

**4) Passing a message as an argument:** If the message is passed to the console.log() function, the message will be displayed by the function.

**Code #4:**

```
<script> 
console.log("This is my World"); 
</script> 
```

**5) Passing a function as an argument:** If the function is passed to the console.log() function, then the function displays the passed function() value.

**Code #5:**

```
<script> 
function func() { return (5 * 19); } 
console.log(func()); 
</script> 
```

**6) Passing a number with message as an argument:** If the number is passed to console.log(), it will be displayed by the function along with the message given.

**Code #6:**

```
<script> 
var a = 2; 
console.log("The value of a is " + a); 
</script> 
```

**7) Passing a string with message as an argument:** If the string is passed to console.log(), it will be displayed by the function along with the message given.

**Code #7:**

```
<script> 
var str = "This is my World"; 
console.log("The value of str is " + str); 
</script> 
```

**8) Passing a char with message as an argument:** If the char is passed to console.log(), it will be displayed by the function along with the message given.

**Code #8:**

```
<script> 
var ch = '2'; 
console.log("The value of ch is " + ch); 
</script> 
```