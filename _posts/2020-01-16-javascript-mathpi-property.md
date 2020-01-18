---
image: "/assets/default-social-image.png"
title: JavaScript Math.PI Property
categories: JavaScript-math
---

The Math.PI is a JavaScript property that is merely used to find Pi's value, i.e. in symbolic form, which is nothing more than the circumference ratio of a circle to its diameter, the value of which is about 3.1416. It is used specifically for a math problem.

**Variations between property and function**

JavaScript property is nothing but a value while method is a function which can be interpreted with the help of below provided example:

```
<script>  
  
// car is an object.  
var car = {};  
  
// car.name is a property of the given object.  
car.name = "Audi",  
  
    // car.sayModel is a function of the given object.  
    car.sayModel = function() {  
        document.write("A8 <br>");  
    }  
                  
    // printing property value.  
    document.write(car.name + '<br>');  
                  
car.sayModel();      
</script>  
```

Output:

```
Audi
A8
```

Here as we can see the object car's property, the string will be stored as "Audi" and accessible by car.name.

sayModel is a method i.e. an object function and can be obtained by using car.sayModel().

It can be noted that sayModel is merely a function that uses ().

**Syntax:**

`Math.PI`

**Parameters:**

Nothing is passed here as a parameter, as Math. PI is not a function but a property.

**Return values:**

It just returns the PI value i.e Π.

Example:

```
Input : Math.PI
Output: 3.141592653589793
```

**Explanation:**

Here the PI value is merely expressed in output.

Example 1:

```
<script> 
  // Here value of Math.PI is printed. 
  document.write(Math.PI); 
</script> 
```

Output:

`3.141592653589793`

Example 2:

PI value i.e. Π, can be displayed as shown below in the form of a function.

```
<script> 
  // function is being called. 
  function get_Value_of_PI() 
  { 
      return Math.PI; 
  } 
  
  // function is calling. 
  document.write(get_Value_of_PI()); 
</script> 
```

Output:

`3.141592653589793`

**Errors and Exceptions:**

Here we consider Math.PI as a function but in reality, it is a property which is why error is displayed in output.

```
<script> 
  // Here we consider Math.PI as a function but 
  // in actual it is a property that is why error 
  // as output is being shown. 
  document.write(Math.PI(12)); 
</script> 
```

Output:

`Error: Math.PI is not a function`

**Application:**

We take the help of this property whenever we need to find the value of anything linked to PI each time.  It is used a lot In math problems.

Example:

The value of the area of a circle with the given value of its radius will be calculated here.

```
<script> 
  // function is being called with radius 5 as parameter. 
  function area_of_circle(radius_of_the_circle) 
  { 
      return Math.PI * radius_of_the_circle * radius_of_the_circle; 
  } 
  
  // Here area of the circle is 5 unit. 
  document.write(area_of_circle(5)); 
</script> 
```

Output:

`78.53981633974483`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari