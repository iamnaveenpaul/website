---
image: "/assets/default-social-image.png"
title: JavaScript typeof operator
categories: JavaScript-operators
---

The typeof operator returns the operand's data type in the form of a string in JavaScript. Operand can be any object, variable or function.

Syntax:

```
typeof operand
      OR
typeof (operand)
```

Examples:

```
Input: typeof "griva"
Output: string

Input: typeof NaN
Output: number
NaN is also considered as a number.
```

```
<!DOCTYPE html> 
<html> 
<body> 
<p id="ABC"></p> 
<script> 
document.getElementById("ABC").innerHTML =  
    typeof "Siddharth" + "<br>" + 
    typeof 3.14 + "<br>" + 
    typeof true + "<br>" + 
    typeof NaN + "<br>" + 
    typeof [5, 10, 15, 20] + "<br>" + 
    typeof {name:'Siddharth', age:20} + "<br>" + 
    typeof new Date() + "<br>" + 
    typeof function () {} + "<br>" + 
    typeof workout + "<br>" + 
    typeof null; 
</script> 
</body> 
</html> 
```

Output:

```
string
number
boolean
number
object
object
object
function
undefined
object
```