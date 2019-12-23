---
title: JavaScript match()
image: "/assets/default-social-image.png"
categories: JavaScript-functions
---

The string.match() is a built-in feature in JavaScript that is used to scan a string for a match against any regular expression and if the match is found, it returns the match as an array.

**Syntax:**

string.match(regExp)

Parameters: The parameter here is "regExp", i.e. regular expression relative to the string specified.

Return Value: returns an array consisting the matches of one element for each match or returns Null if the match is not discovered.

Code to show the working of match() function:

Example 1:

```
Input: 
var string = Welcome to world for world!
document.write(string.match(/rld/g);
```

Output:

`rld, rld`

In the above example, the substring "rld" matches the given string and returns an array of string objects when match is found. Here "g" flag means that all possible matches in a list should be checked for the regular expression.

**code #1:**

```
<script> 
  
    // initializing function to demonstrate match() 
    // method with "g" para 
    function matchString() { 
        var string = "Welcome to world for world"; 
        var result = string.match(/rld/g); 
        document.write("Output : " + result); 
    } matchString(); 
      
</script> 
```

Output:

`rld, rld`

Example 2:

```
Input:
var string = "Welcome to WORLD for world!";
document.write(string.match(/rld/i);
```

Output:

`RLD`

In the illustration above, the substring "rld" matches the specified string and if it recognizes the match, it will return immediately. Here the parameter "i" helps in the provided string to find the case-sensitive match.

**Code #2:**

```
<script> 
  
    // initializing function to demonstrate match() 
    // method with "i" para 
    function matchString() { 
        var string = "Welcome to WORLD for world!"; 
        var result = string.match(/rld/i); 
        document.write("Output : " + result); 
    } matchString(); 
      
</script> 
```

Output:

`RLD`

Example 3:

```
Input:
var string = "Welcome to WORLD for world!";
document.write(string.match(/rld/gi);
```

Output:

`RLD, rld`

In the illustration above, the substring "rld" matches the provided string and if it recognizes the match, it will return immediately. Here the "gi" parameter allows in the specified string to locate the case-sensitive match as well as any combination.

**Code #3:**

```
<script> 
  
    // initializing function to demonstrate match() 
    // method with "gi" para 
    function matchString() { 
        var string = "Welcome to WORLD for world!"; 
        var result = string.match(/rld/gi); 
        document.write("Output : " + result); 
    } matchString(); 
      
</script> 
```

Output:

`RLD, rld`