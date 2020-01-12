---
image: "/assets/default-social-image.png"
title: JavaScript String includes() Method
categories: JavaScript-strings
---

In JavaScript, the function includes() decides whether or not a string includes the specified characters inside it. This method returns true if the characters are contained in the string or else it returns false.

Note: The includes() approach is case sensitive i.e. it will handle the characters of Uppercase and Lowercase types in a different manner.

**Syntax:**

`string.includes(searchvalue, start)`

**Parameters Used:**

* **search value:** It is the series the search will be performed in.
* **start:** It is the position from which the scan will be processed (although this parameter is not required unless this is mentioned, the search will start from the beginning of the string).

**Return Value:**

Returns either a Boolean true, suggesting the existence, or a false implying the exclusion.

Examples:

```
Input : Welcome to GrivaForCoding.
        str.includes("Griva");


Output : true
```

The search must take place from the starting index, since the second parameter is not specified. And it's going to search for Griva, it's going to return a true as it is present in the string.

```
Input: Welcome to GrivaForCoding.


Output: false
```

The second parameter is not described even in this case, therefore the scan will occur from the beginning index. But since this method is case sensitive, the two strings will be handled differently, thus returning a boolean false. Since that is case sensitive.

Code 1:

```
<!DOCTYPE html> 
<html> 
<body> 
<p id="GFC"></p> 
<script> 
  
    var str = "Welcome to GrivaForCoding."; 
    var check = str.includes("Griva"); 
    document.getElementById("GFC").innerHTML = check; 
  
</script> 
  
</body> 
</html> 
Output : false
```

Code 2:

```
<!DOCTYPE html> 
<html> 
<body> 
<p id="GFC"></p> 
<script> 
  
    var str = "Welcome to GrivaForCoding."; 
    var check = str.includes("griva"); 
    document.getElementById("GFC").innerHTML = check; 
  
</script> 
  
</body> 
</html> 
Output : false
```

Code 3:

```
<!DOCTYPE html> 
<html> 
<body> 
<p id="GFC"></p> 
<script> 
  
    var str = "Welcome to GrivaForCoding."; 
    var check = str.includes("o", 17); 
    document.getElementById("GFC").innerHTML = check; 
  
</script> 
</body> 
</html> 
Output : true
```

Code 4:

```
<!DOCTYPE html> 
<html> 
<body> 
<p id="GFC"></p> 
<script> 
  
    var str = "Welcome to GrivaForCoding."; 
    var check = str.includes("o", 18); 
    document.getElementById("GFC").innerHTML = check; 
  
</script> 
  
</body> 
</html> 
Output : false
```

Exceptions :

The check will not be performed if the second parameter, i.e. the measured index (start index) is greater than or equal to the length of the string and therefore returns false.

```
<!DOCTYPE html> 
<html> 
<body> 
<p id="GFC"></p> 
<script> 
  
    var str = "Welcome to GrivaForCoding."; 
    var check = str.includes("o", 25); 
    document.getElementById("GFC").innerHTML = check; 
  
</script> 
  
</body> 
</html> 
Output : false
```

If the measured index (starting index) i.e. the position where the lookup starts is less than 0, then the whole array will be checked.

```
<!DOCTYPE html> 
<html> 
<body> 
<p id="GFC"></p> 
<script> 
  
    var str = "Welcome to GrivaForCoding."; 
    var check = str.includes("o", -2); 
    document.getElementById("GFC").innerHTML = check; 
  
</script> 
  
</body> 
</html> 
Output : true
```