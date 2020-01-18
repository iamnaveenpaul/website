---
image: "/assets/default-social-image.png"
title: JavaScript Math.SQRT2 property
categories: JavaScript-math
---

The Math.SQRT2 is a JavaScript property which is basically used to calculate the value of square root 2, the value which is about 1.4142. That is,

`√ 2  = 1.4142`

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

`Math.SQRT2;`

**Parameters:**

Nothing is passed here as a parameter, as Math.SQRT2 is not a function but a property.

**Return Values:**

This essentially returns the value of the square root of 2, the value of which is roughly 1.4142.

Example:

```
Input : Math.SQRT2
Output: 1.4142135623730951
```

**Explanation:**

The value of the square root of 2 is simply shown as output here.

Example 1:

```
<script> 
  // Here value of Math.SQRT2 is printed. 
  document.write(Math.SQRT2); 
</script> 
```

Output:

`1.4142135623730951`

Example 2:

Square root value of 2 can be displayed in function form as shown below.

```
<script> 
  // function is being called. 
  function get_Value_of_square_root() 
  { 
      return Math.SQRT2; 
  } 
  
  // function is calling for getting 
  // value of square root of 2 
  document.write(get_Value_of_square_root()); 
</script> 
```

Output:

`1.4142135623730951`

**Errors and Exceptions:**

Here we assume Math.SQRT2 as a function, but in fact it is a property which is why error is displayed in the output

Example:

```
<script> 
  // Here we consider Math.SQRT2 as a function  
  //but in actual it is a property that is why error 
  // as output is being shown. 
  document.write(Math.SQRT2(12)); 
</script> 
```

Output:

`Error: Math.SQRT2 is not a function`

**Application:**

It's purpose is to find the square root value of 2 that is accomplished with the help of this property. It's helpful a lot In math problems.

Example:

```
<script> 
  // Value of Math.SQRT2 is printed. 
  document.write(Math.SQRT2); 
</script> 
```

Output:

`1.4142135623730951`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari