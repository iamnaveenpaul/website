---
image: "/assets/default-social-image.png"
title: JavaScript String endsWith()
categories: JavaScript-strings
---

The str.endsWith() method is used to test whether the provided string ends with the required string characters, or not.

**Syntax:**

`str.endsWith(searchString, length)`

**Arguments**

The first argument to this method is a searchString string of characters that is to be retrieved at the end of the specified string. The second argument to the method is length that defines the length of the specified array to be checked for the searchString from the beginning.

**Return value**

This function returns the boolean value true if the searchString is found else the boolean value is returned false.

Example 1:

```
var str = 'It is a great day.'
print(str.endsWith('day.'));
```

Output:

`true`

In this illustration, the searchString method endsWith() checks at the end of the specified string. Hence this function returns true, since the searchString is found at the end.

Example 2:

```
var str = 'It is a great day.'
print(str.endsWith('great'));
```

Output:

`false`

In this example the searchString method endsWith() checks at the end of the given string. Therefore this function returns false since the searchString is not located at the end.

Example 3:

```
var str = 'It is a great day.'
print(str.endsWith('great',13));
```

Output:

`true`

In this illustration, the searchString method endsWith() checks at the end of the specified string. Because the second argument specifies the end of the string at index 13, and searchString is found to end at this point, this method thus returns true.

Program 1:

```
<script> 
// JavaScript to illustrate endsWith() function 
function func() { 
  
    // Original string 
    var str = 'It is a great day.'; 
  
    // Finding the search string in the 
    // given string  
    var value = str.endsWith('day.');   
    document.write(value); 
} 
func(); 
</script> 
print(value);  
```

Output:

`true`

Program 2:

```
// JavaScript to illustrate endsWith() function 
<script> 
function func() { 
  
    // Original string 
    var str = 'It is a great day.'; 
  
    // Finding the search string in the 
    // given string  
    var value = str.endsWith('great'); 
    document.write(value);  
} 
func(); 
</script> 
```

Output:

`false`

Program 3:

```
<script> 
// JavaScript to illustrate endsWith() function 
function func() { 
  
    // Original string 
    var str = 'It is a great day.'; 
  
    // Finding the search string in the  
    // given string  
    var value = str.endsWith('great',13); 
    document.write(value);   
} 
func(); 
</script>  
```

Output:

`true`