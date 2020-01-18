---
title: JavaScript Math.SQRT1_2 property
image: "/assets/default-social-image.png"
categories: JavaScript-math
---

The Math.SQRT1_2 is a JavaScript property that is essentially used to calculate the value of 1/2 square root, whose value is about 0.707106. That is,

`√ (1/2)  = 0.707106`

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

`Math.SQRT1_2;`

**Parameters:**

Nothing is passed here as a parameter, as Math.SQRT1_2 is not a function but a property.

**Return Values:**

It simply returns the square root value of 1/2 which is about 7071.

Example:

```
Input  : Math.SQRT1_2
Output : 0.7071067811865476
```

Explanation:

Here the square root value of 1/2 is simply displayed in the output.

Example 1:

```
<script> 
  // Here value of SQRT1_2 is printed. 
  document.write(Math.SQRT1_2); 
</script> 
```

Output:

`0.7071067811865476`

Example 2:

Value of 1/2 square root may be displayed as in function form:

```
<script> 
  // function is being called. 
  function get_Value_of_square_root() 
  { 
     return Math.SQRT1_2; 
  } 
  // function is calling for getting 
  // value of square root of 1/2 
  document.write(get_Value_of_square_root()); 
</script> 
```

Output:

`0.7071067811865476`

**Errors and Exceptions:**

Here we consider Math.SQRT1_2 as a function but it is actually a property which is why error is shown as output.

Example:

```
<scripe> 
  // Here we consider Math.SQRT1_2 as a function 
  //but in actual it is a property that is why  
  //error as output is being shown. 
  document.write(Math.SQRT1_2(12)); 
</scripe> 
```

Output:

`Error: Math.SQRT1_2 is not a function`

**Application:**

It's implemented to find the square root value of 1/2 that is achieved with the help of this property. It's required a lot in math problems.

Example:

```
<script> 
  // Value of Math.SQRT1_2 is printed. 
  document.write(Math.SQRT1_2); 
</script> 
```

Output:

`0.7071067811865476`

**Supported Browsers:**

* Google Chrome
* Interent Explorer
* Firefox
* Opera
* Safari