---
title: JavaScript array.reduceRight()
image: "/assets/default-social-image.png"
categories: JavaScript-array
---

The array.reduceRight() is a built-in feature in JavaScript that is used to transform elements of the specified array to a single value from right to left.

**Syntax:**

`array.reduceRight(previousValue, currentValue)`

**Parameters:** It accepts two previousValue and currentValue parameters that reflect the preceding and current element of the provided input array.

**Return Values:** Upon reduction, it returns the result to a single value.

Code #1:

```
<script> 
  
// Taking some array as the element of an array "A" 
const A = [ [ 1, 2, 3 ], [ 4, 5, 6 ], [ 7, 8 ] ]; 
  
// Calling array.reduceRight() function 
a = A.reduceRight((previousValue, currentValue) => previousValue.concat(currentValue)); 
  
// printing result 
document.write(a); 
  
</script> 
```

Output:

`7, 8, 4, 5, 6, 1, 2, 3`

Code #2:

```
<script> 
  
// Taking some array as the element of an array "A" 
const A = [ [ 1, 2, 3 ], [ "a", "b", "c" ], [ 7, 8 ] ]; 
  
// Calling array.reduceRight() function 
a = A.reduceRight((previousValue, currentValue) => previousValue.concat(currentValue)); 
  
// printing result 
document.write(a); 
  
</script> 
```

Output:

`7, 8, a, b, c, 1, 2, 3`