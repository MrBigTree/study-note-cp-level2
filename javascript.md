
### OOP

```javascript
class Dog {
  //constructor
  constructor(name) {
    this.name = name;
  }
  //method
  bark() {
    console.log(`${this.name} says woof!`);
  }
}
const myDog = new Dog('Buddy');
myDog.bark(); // Buddy says woof!

```

### Set

A collection of values where each value must be unique.

```javascript
// you are given an array wth duplicated numbers
const numbers = [1, 2, 3, 4, 5, 2, 3, 6, 7, 8, 4, 9];

// Create a Set from the numbers array
const uniqueNumbersSet = new Set(numbers);

// Convert the Set back to an array
const uniqueNumbersArray = [...uniqueNumbersSet];

console.log(uniqueNumbersSet); // Set {1, 2, 3, 4, 5, 6, 7, 8, 9}
console.log(uniqueNumbersArray); // [1, 2, 3, 4, 5, 6, 7, 8, 9]

```
### Map

A collection of key-value pairs.

```javascript
const ages = new Map();
ages.set('Alice', 25);
ages.set('Bob', 30);
console.log(ages.get('Alice')); // 25
```
### Import/Export

Used to split code into multiple modules and reuse them.

```javaScript
// math.js
export function add(x, y) {
  return x + y;
}

// app.js
import { add } from './math.js';
console.log(add(2, 3)); // 5

```


SetTimeOut

Promise

Resolve

Reject

Then/Catch

Async

Await


Bind 


Imperative


## this keyword

In JavaScript, the `this` keyword is a special identifier that automatically gets a value assigned, depending on where and how a function is called. It generally refers to an object and provides a way to access properties and methods of that object within the function. Understanding the behavior of `this` can be a bit tricky because its value can change based on the context in which a function is called.

Here's a breakdown of how `this` behaves in different scenarios:

1. **Global Context**:
   In the global context (outside of any function), `this` refers to the global object. In a browser, the global object is `window`.
   ```javascript
   console.log(this === window);  // true
   ```

2. **Inside a Regular Function**:
   When a function is called in the usual way (not as a method, constructor, or arrow function), `this` refers to the global object.
   ```javascript
   function regularFunction() {
       console.log(this === window);  // true
   }
   regularFunction();
   ```

3. **Inside a Method**:
   When a function is defined on an object and is called as a method of that object, `this` refers to the object.
   ```javascript
   const obj = {
       method: function() {
           console.log(this === obj);  // true
       }
   };
   obj.method();
   ```

4. **Inside a Constructor**:
   When a function is used as a constructor (called with the `new` keyword), `this` refers to the newly created instance.
   ```javascript
   function ConstructorFunction() {
       this.value = "I am an instance.";
   }
   const instance = new ConstructorFunction();
   console.log(instance.value);  // "I am an instance."
   ```

5. **Inside an Arrow Function**:
   Arrow functions don't have their own `this` value. Instead, they inherit `this` from the surrounding (lexical) context.
   ```javascript
   const obj = {
       value: "I am obj.",
       method: function() {
           const arrowFunction = () => {
               console.log(this === obj);  // true
           };
           arrowFunction();
       }
   };
   obj.method();
   ```

6. **Using `call()`, `apply()`, and `bind()`**:
   These are methods available on all functions that allow you to explicitly set the value of `this`.
   ```javascript
   function showValue() {
       console.log(this.value);
   }
   const objA = { value: "A" };
   const objB = { value: "B" };
   
   showValue.call(objA);  // "A"
   showValue.apply(objB);  // "B"
   
   const boundFunction = showValue.bind(objA);
   boundFunction();  // "A"
   ```

7. **Inside Event Handlers**:
   In DOM event handlers, `this` typically refers to the element that the event was attached to.
   ```javascript
   button.addEventListener('click', function() {
       console.log(this === button);  // true
   });
   ```

Understanding the behavior of `this` is crucial when working with JavaScript, especially when dealing with object-oriented patterns, event handlers, or certain frameworks and libraries. It's also a common source of confusion for developers new to the language.

## Base64

`Base64` is a binary-to-text encoding scheme that represents binary data in an ASCII string format. It is commonly used for encoding data that goes over a network or is used in textual formats that do not support binary data, such as JSON or XML.

The name "Base64" originates from the fact that it uses a 64-character set to represent data, which includes uppercase letters (A-Z), lowercase letters (a-z), numbers (0-9), plus (+), and slash (/). The equal sign (=) is used as a padding character.

**Key Points about Base64**:

1. **Purpose**: Base64 is not encryption; it's an encoding. Its primary purpose is to transform binary data into a string format that can be easily transmitted or stored.

2. **Size**: Encoding data in Base64 increases its size by approximately 33%. This is because every three bytes of binary data are represented as four bytes of Base64-encoded text.

3. **Common Uses**:
   - **Data URIs**: Base64 can be used in data URIs in HTML and CSS to embed small images, fonts, or other assets directly within a document.
   - **Email**: Email protocols are text-based and don't handle binary data well, so attachments are often encoded in Base64.
   - **Tokens**: Some tokens, like JWT (JSON Web Tokens), use Base64 encoding for their payload.

4. **Encoding and Decoding**: Many programming languages provide functions or libraries to encode and decode Base64. For example, in JavaScript, you can use `btoa()` to encode and `atob()` to decode.

**Example**:

In JavaScript:

```javascript
let encodedData = btoa("Hello, World!");  // Encode a string
console.log(encodedData);  // Outputs: "SGVsbG8sIFdvcmxkIQ=="

let decodedData = atob(encodedData);  // Decode the encoded data
console.log(decodedData);  // Outputs: "Hello, World!"
```

It's important to note that while Base64 encoding can obscure data, it should not be relied upon for security or encryption purposes. Anyone can easily decode Base64-encoded data. If you need to protect or secure information, you should look into proper encryption techniques.

## JQuery

jQuery is a fast, small, and feature-rich JavaScript library. It makes things like HTML document traversal and manipulation, event handling, and animation much simpler with an easy-to-use API that works across a multitude of browsers. With a combination of versatility and extensibility, jQuery has changed the way millions of people write JavaScript.

Here's a basic introduction to jQuery:

### 1. **Why Use jQuery?**
- **Simplify common tasks**: jQuery provides methods to handle common client-side tasks without writing a lot of JavaScript.
- **Cross-browser compatibility**: jQuery handles a lot of the quirks between browsers, so you don't have to.

### 2. **Getting Started**:
To use jQuery, you first need to include it in your project. You can download it from [jQuery's website](https://jquery.com/) or include it via a CDN (Content Delivery Network).

```html
<!-- Including jQuery from Google's CDN -->
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
```

### 3. **Basic Syntax**:
The basic syntax of jQuery is `$(selector).action()`.
- `$`: Defines/accesses jQuery.
- `(selector)`: Finds HTML elements.
- `.action()`: Executes an action on the elements.

### 4. **Examples**:

**Document Ready Event**:
Ensures that code doesn't run until the document is fully loaded.
```javascript
$(document).ready(function(){
   // Your code here
});
```

**Selecting Elements**:
```javascript
$("#id");           // Selects element with id="id"
$(".class");        // Selects all elements with class="class"
$("element");       // Selects all <element> elements
```

**Event Handling**:
```javascript
$("button").click(function(){
    alert("Button was clicked!");
});
```

**Manipulating Content**:
```javascript
$("#some-id").text("New text");              // Sets the text of an element
$("#some-id").html("<b>New HTML</b>");       // Sets the inner HTML of an element
$("#some-input").val("New Value");           // Sets the value of an input field
```

**Manipulating Attributes**:
```javascript
$("a").attr("href", "https://www.example.com");   // Sets the href attribute of all <a> tags
```

**Adding/Removing Classes**:
```javascript
$("p").addClass("myClass");       // Adds a class to all <p> elements
$("p").removeClass("myClass");    // Removes a class from all <p> elements
```

**Animations**:
```javascript
$("#some-id").hide();             // Hides an element
$("#some-id").show();             // Shows an element
$("#some-id").toggle();           // Toggles visibility of an element
$("#some-id").fadeOut();          // Fade out an element
$("#some-id").fadeIn();           // Fade in an element
```

### 5. **AJAX with jQuery**:
jQuery simplifies the process of making AJAX requests.

```javascript
$.ajax({
  url: "https://api.example.com/data",
  type: "GET",
  dataType: "json",
  success: function(data) {
    console.log(data);
  },
  error: function(error) {
    console.error("Error fetching data:", error);
  }
});
```

### 6. **Advantages**:
- **Simplicity**: jQuery's syntax is clear and concise.
- **Large community**: There are countless resources, plugins, and tutorials available.
- **Extensibility**: jQuery can be extended with plugins to add additional functionality.

### 7. **Considerations**:
While jQuery is powerful and popular, it's essential to note that modern browsers have come a long way, and many tasks that once required jQuery can now be done with vanilla JavaScript. Additionally, with the rise of modern JavaScript frameworks like React, Angular, and Vue.js, the need for jQuery in new projects has diminished. However, it remains a valuable tool, especially for maintaining older projects or for those who prefer its syntax and capabilities.