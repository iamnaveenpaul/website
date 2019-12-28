---
image: "/assets/default-social-image.png"
title: JavaScript array.toLocaleString() function
categories: JavaScript-array
---

The array.toLocaleString() is a JavaScript built-in function that is used to convert the element of the specified array to string.

**Syntax:**

`arr.toLocaleString();`

**Return values:**

It returns a string containing the array's components.

**JavaScript Version:**

ECMAScript 1

Examples:

```
Input: 
var name = "gfg";
var number = 123;
var A = [ name, number ];
Output:
> "gfg, 123"
```

There as we see two variables representing elements in the input but these are converted into a string in the output.

```
// taking inputs. 
var name = "griva"; 
var number = 567; 
  
// It will give current date and time. 
var date = new Date(); 
  
// Here A is an array containing elements of above variables. 
var A = [ name, number, date ]; 
  
// applying array.toLocaleString function. 
var string = A.toLocaleString(); 
  
// printing string. 
console.log(string); 
```

Output:

`> "griva, 567, 2/18/2018, 10:41:20 AM"`

**Application:**

The JavaScript array.toLocaleString() method is used whenever the element of the specified array is to be converted to a string.

```
// taking inputs. 
var name = [ "Ram", "Sheeta", "Geeta" ]; 
var number1 = 3.45; 
var number2 = [ 23, 34, 54 ]; 
  
// Here A is an array containing elements of above variables. 
var A = [ name, number1, number2 ]; 
  
// appling array.toLocaleString function. 
var string = A.toLocaleString(); 
  
// printing string. 
console.log(string); 
```

Output:

`> "Ram, Sheeta, Geeta, 3.45, 23, 34, 54"`