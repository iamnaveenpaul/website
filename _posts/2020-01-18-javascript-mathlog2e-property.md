---
image: "/assets/default-social-image.png"
title: JavaScript Math.LOG2E property
categories: JavaScript-math
---

The Math.LOG2E is a JavaScript property that is useful to find the value of base 2 logarithms of e, where e is an irrational and transcendental number roughly equivalent to 2.718

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

`Math.LOG2E;`

**Parameters:**

Since Math.LOG2E is not a function, nothing is as a parameter as it is a property.

**Return Values:**

This simply returns the logarithm of base 2 value of e.

Example:

```
Input : Math.LOG2E
Output:1.4426950408889634
```

Explanation:

The value of base 2 logarithm of e is actually shown as output here.

Example 1:

```
<script> 
  // Here value of Math.LOG2E is printed. 
  document.write(Math.LOG2E); 
</script> 
```

Output:

`1.4426950408889634`

Example 2:

Value of base 2 logarithm of e can be written as shown below in function form:

```
<script> 
  // function is being called. 
  function get_Value_of_base_2_lagarithm_of_e() 
  { 
      return Math.LOG2E; 
  } 
  
  // function is calling. 
  document.write(get_Value_of_base_2_lagarithm_of_e()); 
</script> 
```

Output:

`1.4426950408889634`

Example 3:

We consider Math.LOG2E as a function here, but in reality it is a property which is why error is displayed as output.

```
<script> 
  // Here we consider Math.LOG2E as a function but  
  //in actual it  is a property that is why error  
  //as output is being shown. 
  document.write(Math.LOG2E(12)); 
</script> 
```

Output:

`Error: Math.LOG2E is not a function`

**Application:**

We take the help of this property whenever we need to find the value of base 2 logarithm of e that time. It is usually helpful in math problems.

Example:

```
<script> 
  // Value of Math.LOG2E is printed. 
  document.write(Math.LOG2E); 
</script> 
```

Output:

`1.4426950408889634`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari