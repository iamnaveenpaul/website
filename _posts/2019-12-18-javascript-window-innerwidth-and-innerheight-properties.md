---
image: "/assets/default-social-image.png"
title: JavaScript Window innerWidth and innerHeight Properties
categories: JavaScript-basics
---

JavaScript's innerWidth property returns the width, and the innerHeight property returns the screen display field height.

**Syntax:**

```
window.innerWidth
window.innerHeight
```

Parameter: No parameters are needed.

Return Value: returns a number, which represents the width and height of the content area of the window.

Note: Using clientWidth and clientHeight to get the width and height of the screen for IE 8 i.e. (Internet Edg 8) or earlier.

Example:

```
<!DOCTYPE html> 
<html> 
     <head> 
          <title>Browser Inner width and height</title> 
          <style> 
            body{ 
                text-align:center; 
            } 
            .gfg { 
                font-size:40px; 
                font-weight:bold; 
                color:green; 
            } 
          </style> 
     </head> 
     <body> 
     <div class = "gfg">GeeksforGeeks</div> 
     <h2>Browser Window</h2> 
     <p id="demo"></p> 
     <script> 
          var Width, Height, result; 
  
          // height and width of Browser window 
          Width = window.innerWidth || document.documentElement.clientWidth 
                  || document.body.clientWidth; 
  
          Height = window.innerHeight || document.documentElement.clientHeight 
                  || document.body.clientHeight; 
          // Display Width and Height. 
          result = document.getElementById("demo"); 
          result.innerHTML = "Browser inner width: " + Width + 
                              "<br>Browser inner height: " + Height; 
  
     </script> 
</body> 
</html> 
```