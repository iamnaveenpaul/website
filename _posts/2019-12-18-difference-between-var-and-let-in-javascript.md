---
image: "/assets/default-social-image.png"
title: Difference between var and let in JavaScript
categories: JavaScript-basics
---

**Difference between var and let in JavaScript**

Both var and let are used in javascript variable declarations but the distinction between them is that var is function scoped and let is block scoped.

It is possible to say that a variable specified with var is defined as opposed to let throughout the program.

To clarify the difference even better

Example of var:

```
Input:
console.log(x);
var x=5;
console.log(x);
```

Output:

```
undefined
5
```

Example of let:

```
Input:
console.log(x);
let x=5;
console.log(x);
```

Output:

`Error`

Let’s see code in JavaScript:

**Code #1:**

```
<html> 
  
<body> 
    <script> 
        // calling x after definition 
        var x = 5; 
        document.write(x, "\n"); 
  
        // calling y after definition  
        let y = 10; 
        document.write(y, "\n"); 
  
        // calling var z before definition will return undefined 
        document.write(z, "\n"); 
        var z = 2; 
  
        // calling let a before definition will give error 
        document.write(a); 
        let a = 3; 
    </script> 
</body> 
  
</html> 
```

**Code #2:**

Clicking start will call a function in the following code, which will change the color of the two headings at the rate of 0.5sec. The first heading color is placed in a var and let is used to declare the second.

Then both are accessed outside of the function block. Var is going to work, but the variable defined using let is going to show an error as let is block scoped.

```
<!DOCTYPE html> 
<html> 
  
<head> 
    <title>Var vs Let</title> 
</head> 
  
<body> 
  
    <h1 id="var" style="color:black;">ThisIsMyWorld</h1> 
    <h1 id="let" style="color:black;">ThisIsStillMyWorld</h1> 
    <button id="btn" onclick="colour()">Start</button> 
    <!-- executing function on button click -->
  
    <script type="text/javascript"> 
        function colour() { 
  
            setInterval(function() { 
  
                if (document.getElementById('var').style.color == 'black') 
                    var col1 = 'blue'; 
                else 
                    col1 = 'black'; 
  
                // setting value of color 1 through var 
  
                if (document.getElementById('let').style.color == 'black') { 
                    let col2 = 'red'; 
                } else { 
                    col2 = 'black'; 
                } 
  
                // setting value of color 2 through let 
  
                document.getElementById('var').style.color = col1; 
  
                document.getElementById('let').style.color = col2; 
  
                // changing color of h1 in html 
            }, 500); 
  
        } 
    </script> 
</body> 
  
</html> 
```