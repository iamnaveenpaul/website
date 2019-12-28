---
image: "/assets/default-social-image.png"
title: JavaScript Array concat()
categories: JavaScript-array
---

The method Array.concat() is used to merge two or more arrays. This function does not change the original arrays that were passed as arguments.

**Syntax:**

`var new_array = old_array.concat(value1[, value2[, ...[, valueN]]])`

**Arguments:**

The arguments for this function are the arrays or values to apply to the specified array. To this function, the number of arguments depends on the number of arrays or values to be combined.

**Return value:**

This function returns a newly created array created after all the arrays passed as arguments to the function have been merged.

Example 1:

```
var num1 = [11, 12, 13],
    num2 = [14, 15, 16],
    num3 = [17, 18, 19];
print(num1.concat(num2, num3));
```

Output:

`[11,12,13,14,15,16,17,18,19]`

In this case, the concat() method concatenates all three arrays into one array that it returns as an answer.

Example 2:

```
var alpha = ['a', 'b', 'c'];
print(alpha.concat(1, [2, 3]));
```

Output:

`[a,b,c,1,2,3]`

In this case, the concat() function concatenates all the arguments passed with the provided array to the function into one array that it returns as the response.

Example 3:

```
var num1 = [[23]];
var num2 = [89, [67]];
print(num1.concat(num2));
```

Output:

`[23,89,67] `

In this case, the concat() method concatenates the two arrays into one array that it returns as a response.

Program 1:

```
<script> 
// JavaScript code for concat() function 
function func() { 
    var num1 = [11, 12, 13], 
        num2 = [14, 15, 16], 
        num3 = [17, 18, 19]; 
    document.write(num1.concat(num2, num3)); 
} 
func(); 
</script> 
```

Output:

`[11,12,13,14,15,16,17,18,19]`

Program 2:

```
<script> 
// JavaScript code for concat() function 
function func() { 
    var alpha = ['a', 'b', 'c']; 
    document.write(alpha.concat(1, [2, 3])); 
} 
func(); 
</script> 
```

Output:

`[a,b,c,1,2,3]`

Program 3:

```
<script> 
// JavaScript code for concat() function 
function func() { 
    var num1 = [[23]]; 
    var num2 = [89, [67]]; 
    document.write(num1.concat(num2)); 
} 
func(); 
</script>
``` 

Output:

`[23,89,67]`