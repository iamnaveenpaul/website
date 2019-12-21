---
image: "/assets/default-social-image.png"
title: JavaScript Proxy() Object
categories: JavaScript-objects
---

The JavaScript proxy object is used to describe the custom actions of basic operations (e.g. property scan, assignment, enumeration, invocation of functions, etc.).

**Syntax:**

`var p = new Proxy(target, handler);`

Parameter: The object of the proxy recognizes two parameters as follows:

target: A target object to wrap with Proxy (can be any form of object including a function, class, or other proxy).
handler: An object whose properties are functions that determine the proxy's actions when it executes an operation performed on it.

Example:

```
<script> 
const Person = { 
    Name: 'John Nash', 
    Age: 25 
}; 
  
const handler = { 
    // target represents the Person while prop represents 
        // proxy property. 
    get: function(target, prop) { 
        if (prop === 'FirstName') { 
            return target.Name.split(' ')[0]; 
        } 
        if (prop === 'LastName') { 
            return target.Name.split(' ').pop(); 
        } 
        else { 
            return Reflect.get(target,prop); 
        } 
    } 
}; 
  
const proxy1 = new Proxy(Person, handler); 
  
document.write(proxy1 + "<br>"); 
  
// Though there is no Property as FirstName and LastName,  
// still we get them as if they were property not function. 
document.write(proxy1.FirstName + "<br>"); 
document.write(proxy1.LastName  + "<br>"); 
</script> 
```

Output:

```
[object Object]
John
Nash
```

Note: When NodeJs is installed, the above code can be executed directly in the terminal, otherwise it can be executed in an HTML file by pasting the above in the script tag and testing the console output of any web browser.