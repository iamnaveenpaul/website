---
image: "/assets/default-social-image.png"
title: JavaScript String startsWith() Method
categories: JavaScript-strings
---

The str.startsWith() method is used to examine if the given string begins with the specified string characters or not.

**Syntax:**

`str.startsWith( searchString , position )`

**Parameters:**

This method accepts two parameters as described below:

* **searchString:** Parameter needed. It stores the string that needs to be searched.
* **start:** It specifies the position from which the searchString is to be checked in the given string. The default value is zero.

**Return value:**

This method returns the boolean value true if identified, or else searchString returns false.

Example 1:

```
var str = 'It is a great day.';
var value = str.startsWith('It'); 
print(value);
```

Output:

`true`

The function startsWith() in the above case, tests whether or not the string str begins with It. Therefore it returns true since the string begins with It.

Example 2:

```
var str = 'It is a great day.';
var value = str.startsWith('great');
print(value);
```

Output:

`false`

In this case, the startWith() function examines whether or not the string str begins with great. Therefore it returns false because great occurs in the middle and not at the start of the string.

Example 3:

```
var str = 'It is a great day.'
var value = str.startsWith('great',8);
print(value);
```

Output:

`true`

In this illustration, the startWith() function tests whether the string str begins at the defined index 8 with great or not. Because great occurs in the string in the provided index, it returns true.

Program 1:

```
<script> 
// JavaScript to illustrate startsWith() function 
  
function func() { 
       
    // Original string 
    var str = 'It is a great day.'; 
      
    // Checking the condition 
    var value = str.startsWith('It');  
    document.write(value); 
} 
func(); 
</script> 
```

Output:

`true`

Program 2:

```
<script> 
  
// JavaScript to illustrate  
// startsWith() function 
function func() { 
      
    // Original string 
    var str = 'It is a great day.'; 
    var value = str.startsWith('great'); 
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
  
// JavaScript to illustrate 
// startsWith() function 
function func() { 
       
    // Original string 
    var str = 'It is a great day.'; 
    var value = str.startsWith('great', 8); 
    document.write(value); 
} 
  
// Function call 
func(); 
  
</script> 
```

Output:

`true`