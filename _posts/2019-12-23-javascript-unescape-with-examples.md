---
image: "/assets/default-social-image.png"
title: JavaScript unescape() with examples
categories: JavaScript-functions
---

Prerequisite: JavaScript escape(), JavaScript's unescape() function accepts a string as a parameter and uses the string decoded by the escape() function to encode it. In the string, the hexadecimal sequence is substituted by the characters they reflect as unescape() is deciphered.

**Syntax :**

```
<script> 
  
// Special character encoded with 
// escape function 
var str = escape("This is my World!!!"); 
document.write("Encoded : " + str); 
  
// New Line 
document.write("<br>"); 
  
// unescape() function 
document.write("Decoded : " + unescape(str)) 
  
// New Line 
document.write("<br><br>"); 
  
// The exception 
// @ and . not encoded. 
str = escape("To contribute articles contact us" +  
                "at dozenalism@gmail.com") 
document.write("Encoded : " + str); 
  
// New Line 
document.write("<br>"); 
  
// unescape() function 
document.write("Decoded : " + unescape(str)) 
  
</script> 
```

Output :

```
Encoded : This%20is%20my%20world%21%21%21
Decoded : This is my World!!!

Encoded : To%20contribute%20articles%20contact%20us%20at%20dozenalism@gmail.com
Decoded : To contribute articles contact us at dozenalism@gmail.com
```