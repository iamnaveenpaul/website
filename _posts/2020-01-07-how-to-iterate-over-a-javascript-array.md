---
image: "/assets/default-social-image.png"
title: How to iterate over a JavaScript array.
categories: JavaScript-array
---

Single variables in Javascripts are used to store different types of elements.

A simple access to the array for example, may be something like this:

```
<script> 
array = [ 'griva', '4', 'coding' ]; 
  
// Accessing array elements one by one 
console.log(array[0]); 
console.log(array[1]); 
console.log(array[2]); 
</script> 
```

Output:

```
griva
4
coding
```

For Javascript, there are multiple ways you can iterate over an array. Below are the most useful ones.

**Using for loop.**

This is analogous to for loops in other languages such as C / C++, Java, etc.

```
<script> 
array = [ 1, 2, 3, 4, 5, 6 ]; 
for (index = 0; index < array.length; index++) { 
    console.log(array[index]); 
} 
</script> 
```

Output:

```
1
2
3
4
5
6
```

**Using while loop.**

```
<script> 
index = 0; 
array = [ 1, 2, 3, 4, 5, 6 ]; 
  
while (index < array.length) { 
    console.log(array[index]); 
    index++; 
}</script> 
```

Output:

```
1
2
3
4
5
6
```

**using forEach method.**

The forEach method calls the function given once in the order for each array element.

```
<script> 
index = 0; 
array = [ 1, 2, 3, 4, 5, 6 ]; 
  
array.forEach(myFunction); 
function myFunction(item, index) 
{ 
    console.log(item); 
}</script> 
```

Output:

```
1
2
3
4
5
6
```

**Using every method.**

The every() method tests if a parameter (provided as a function) passes all elements in an array.

```
<script> 
index = 0; 
array = [ 1, 2, 3, 4, 5, 6 ]; 
  
const under_five = x => x < 5; 
  
if (array.every(under_five)) { 
    console.log('All are less than 5'); 
} 
else { 
    console.log('At least one element is not less than 5'); 
} 
</script> 
```

Output:

`At least one element is not less than 5.`

**Using map.**

A map applies a function to each element and returns the new array after that.

```
<script> 
index = 0; 
array = [ 1, 2, 3, 4, 5, 6 ]; 
  
square = x => Math.pow(x, 2); 
squares = array.map(square); 
console.log(array); 
console.log(squares);</script> 
```

Output:

```
1 2 3 4 5 6 
1 4 9 16 25 36
```