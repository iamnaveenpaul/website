---
image: "/assets/default-social-image.png"
title: JavaScript Replace() Method
categories: JavaScript-functions
---

JavaScript's replace() function is used to replace the current page with a different page. The Replace Method replaces the current window URL with the Replace Method's URL reference.

**Syntax:**

`location.replace(URL)`

Parameter: Single parameter URL fits this method. The URL is another page reference that needs to be replaced by an older page.

Return Value: restore or open the new window page with this method.

Example:

```
<!DOCTYPE html> 
<html> 
     <head> 
          <title>Redirect to Webpage</title> 
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
     <h2>Replace Method</h2> 
     <button onclick = "Replace()" >Replace with Gfg</button> 
          <script> 
  
               //Replace function that replace the current page. 
               function Replace() { 
                    location.replace("https://www.geeksforgeeks.org/") 
               } 
  
          </script> 
     </body> 
</html> 
```