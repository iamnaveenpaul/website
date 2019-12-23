---
image: "/assets/default-social-image.png"
title: Javascript Window Blur() and Window Focus() Method
categories: JavaScript-function
---

**Window.blur() Method**

To eliminate attention from the current window, the blur() method is used. That is, the new open window gets sent to the background.

**Syntax:**

**Window.blur()**

**Parameter:** It doesn't require any parameters.

**Return Value:** It doesn't Return any value.

**Window.focus() Method**

Focus on the new open window using the focus() method. That's to carry the blur window back to the front.

**Syntax:**

`window.focus()`

**Parameter:** It doesn't require any parameters.

**Return Value:** It doesn't Return any value.

The window.blur() and window.focus() method in JavaScript are illustrated below:

Example:

```
<!DOCTYPE html> 
<html> 
  
<head> 
    <title> 
      window Blur and Focus method 
    </title> 
    <style> 
        body { 
            text-align: center; 
        } 
          
        .gfg { 
            font-size: 40px; 
            font-weight: bold; 
            color: green; 
        } 
    </style> 
</head> 
  
<body> 
    <div class="hello">This is my World</div> 
    <h2>Blur and Focus</h2> 
    <script> 
        var Window; 
  
        // Function that open the new Window  
        function windowOpen() { 
            Window = window.open( 
              "https://www.griva.in/", 
                "_blank", "width=400, height=450"); 
        } 
  
        // function that Closes the open Window  
        function windowClose() { 
            Window.close(); 
        } 
  
        //function that blur the open Window 
        function windowBlur() { 
            Window.blur(); 
        } 
  
        //function that focus on open Window 
        function windowFocus() { 
            Window.focus(); 
        } 
    </script> 
    <button onclick="windowOpen()"> 
      Open Griva 
    </button> 
    <button onclick="windowBlur()"> 
      Blur Griva 
    </button> 
    <button onclick="windowFocus()"> 
      Focus Griva 
    </button> 
    <button onclick="windowClose()"> 
      Close Griva 
     </button> 
</body> 
  
</html> 
```

Output: When you press the blur Griva icon, the tab of griva.in should switch to the background and if you click the focus Griva button, the windows of griva.in should fall to the forefront.

Click on the Blur:


Click on the Focus:


Supported Browser: Window Blur() and Window Focus() supporting browser are described below:

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari