---
image: "/assets/default-social-image.png"
title: JavaScript encodeURI(), decodeURI() and its components functions
categories: JavaScript-basics
---

Encoding and decoding components of URI and the URI is a common task in web development when creating a GET request to the query params API. Most times a URL string is constructed with request parameters and the response server has to decipher this URL in order to understand it. Browsers encrypt the URL internally, i.e. certain unique characters are translated to other reserved characters and then the request is made. For eg, space character " " is transformed to either + or %20.

Example:

* Open www.google.com and write a "geeks for geeks" search query.
* Check at the URL bar of the window until search results arrive. The browser URL in place of space will consist of a %20 or + sign.
* The URL will be shown as follows: https://www.google.com/search?q=geeks%20for%20geeks or https://www.google.com/search?q=geeks+for+geeks

Note: The browser dynamically translated the spaces into + or %20 sign automatically.

There are several other unique characters and it will be tiresome to transform those by hardcode methods. To accomplish this mission, JavaScript provides the following functions:

**encodeURI()**

The function encodeURI() is used to encode the complete URI. This feature encodes unique characters except (, / ? : @ & = + $ #).

**Syntax:**

**encodeURI( complete_uri_string )**

Parameters: This function accepts the complete_uri_string single parameter that is used to hold the encoded URL.

Return Value: The encoded URI returns this function.

Example:

```
<script> 
const url = "https://www.google.com/search?q=geeks for geeks"; 
const encodedURL = encodeURI(url); 
document.write(encodedURL) 
</script> 
```

Output:

`https://www.google.com/search?q=geeks%20for%20geeks`

**encodeURIComponent()**

The encodeURIComponent() function is used to encode certain URI parts or components. This function encodes the characters that are special. It also encodes the following characters: , / ? : @ & = + $ #

**Syntax:**

`encodeURIComponent( uri_string_component )`

Parameters: This feature recognizes the single parameter uri_string_component used to carry the encoded string.

Return Value: The encoded string returns for this function.

Example:

```
<script> 
const component = "geeks for geeks"
const encodedComponent = encodeURIComponent(component); 
document.write(encodedComponent) 
</script> 
```

Output:

`geeks%20for%20geeks`

**decodeURI()**

The function decodeURI() is used to decode the encodeURI() generated URI.

**Syntax:**

`decodeURI( complete_encoded_uri_string )`

Parameters: This feature recognizes the complete_encoded_uri string single parameter containing the encoded string.

Return Value: The decoded string (original string) returns by this function.

Example:

```
<script> 
const url = "https://www.google.com/search?q=geeks%20for%20geeks"; 
const decodedURL = decodeURI(url); 
document.write(decodedURL) 
</script> 
```

Output:

`https://www.google.com/search?q=geeks for geeks`

**decodeURIComponent()**

The function decodeURIComponent() is used to decode certain URI parts or components obtained by encodeURIComponent().

**Syntax:**

`decodeURIComponent( encoded_uri_string_component )`

Parameters: This function accepts the encoded_uri_string component single parameter that holds the encoded string.

Return Value: returns the decoded URI string component.

Example:

```
<script> 
const component = "geeks%20for%20geeks"
const decodedComponent = decodeURIComponent(component); 
document.write(decodedComponent)                     
</script> 
```

Output:

`geeks for geeks`

**Applications:**

* To properly translate space-separated request parameters to the API.
* To decode query parameters of URLs to extract human-readable strings in web scraping.