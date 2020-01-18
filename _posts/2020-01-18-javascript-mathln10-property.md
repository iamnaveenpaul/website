---
image: "/assets/default-social-image.png"
title: JavaScript Math.LN10 property
categories: JavaScript-math
---

The Math.LN10 is a function that is generally used to calculate the value of a natural log of 10. Natural log is of base e which is defined as ln. So, natural log of 10 is described as ln(10) whose value is roughly 2.302

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

`Math.LN10;`

**Parameters:**

Nothing is as a parameter here, as Math.LN10 is not a function but a property

**Return Values:**

This simply returns 10's natural log value.

Examples:

```
Input  : Math.LN10
Output : 2.302585092994046
```

Explanation:

Value of 10 natural log i.e., Math. LN10 is displayed in output.

Example 1:

```
<script> 
  // Here value of Math.LN10 is printed. 
  document.write(Math.LN10); 
</script> 
```

Output:

`2.302585092994046`

Example 2:

Natural log value of 10 can be displayed as in function form as:

```
<script> 
  // function is being called. 
  function get_Value_of_natural_log_of_10() 
  { 
      return Math.LN10; 
  } 
  // function is calling. 
  document.write(get_Value_of_natural_log_of_10()); 
</script> 
```

Output:

`2.302585092994046`

Example 3:

Here we assume Math.LN10 as a function, but in fact it is a property which is why error is shown as output.

```
<script> 
  // Here we consider Math.LN10 as a function but 
  //in actual it is a property that is why error  
  //as output is being shown. 
  document.write(Math.LN10(12)); 
</script> 
```

Output:

`Error: Math.LN10 is not a function`

Note: To check this console checkout after code has been executed.

**Application:**

We take the help of this property if we ever need to calculate the value of the natural log 10 anytime. It is helpful in math problems.

Example:

```
<script> 
  // Value of Math.LN10 is printed. 
  document.write(Math.LN10); 
</script> 
```

Output:

`2.302585092994046`

**Supported Browsers**:

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari