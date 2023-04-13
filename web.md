!!!Review DOM event
no question on bootstrap

1. php database connection
```
<?php
// Database credentials
$host = "localhost";
$user = "username";
$password = "password";
$database = "mydatabase";

// Create connection
$conn = mysqli_connect($host, $user, $password, $database);

// Check connection
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}
echo "Connected successfully";
?>
```
2. url parameters
- also known as query string parameters, are a way to pass data between web pages by appending data to the end of a URL.
- URL parameters are represented by key-value pairs, separated by an equals sign (=) and separated from each other by an ampersand (&). For example, in the URL http://example.com/page.php?name=John&age=30, name=John and age=30 are the URL parameters.

3. get vs post
- GET: The GET method sends data in the URL as a query string. This means that the data is visible in the URL bar of the browser. GET requests are typically used for fetching data FROM the server. 
  - http://example.com/page.php?name=John&age=30
- POST: The POST method sends data in the HTTP request body, which is not visible in the URL bar of the browser. POST requests are typically used for submitting data TO the server.

4. superglobal variable
- $_GET: an array containing the values of all the GET parameters passed to the script.
- $_POST: an array containing the values of all the POST parameters passed to the script.
- $_FILES: an array containing information about the uploaded files, such as the name, type, and temporary location.
- $_COOKIE: an array containing the values of all the cookies sent to the script.
- $_SESSION: This variable is an array containing the values of all the session variables.

5. session and cookie compare
- Session stored in the server is its main advantage than cookie
- Cookie use SSL to ensure data security

6. variable name in js and php
- js is case senstive
- Variable Declaration: JS: var, let, or const; PHP $
- both dynamically typed. PHP is more strict 
- JS: let myVar = 10; const MY_CONST = 'Hello'; var myvar = true;
- PHP: $myVar = 10; define('MY_CONST', 'Hello'); $myvar = true;

7. What does move_uploaded_file() return? 
- move_uploaded_file() function is used in PHP to move uploaded files to a new location.
-  It returns a boolean value indicating whether the operation was successful. If the file is successfully moved, the function returns true, otherwise it returns false.

8. loosely type vs dynamic type
- loosely typed languages allow variables to hold values of any type and the type can be changed at any time, 
- dynamically typed languages determine the type of a variable at runtime based on the value assigned to it.
- a language can be bot loosely and dynamically typed, like js and php
- In some cases, loosely typed and dynamically typed are used interchangeably, but they are not the same thing.

9. is double a data type in js?
- JavaScript represents all numbers, including integers and floating-point numbers, as 64-bit floating-point values 
```
 let x = 5; // integer
 let y = 3.14; // floating-point number
 let z = x + y; // result is a floating-point number
 console.log(z); // outputs 8.14
```
- Note that in JavaScript, you don't need to specify the type of a variable when you declare it. JavaScript is a dynamically typed language, which means that the type of a variable is determined at runtime based on the value assigned to it.

10. php comparsion operator in the code can be trick, loops
- php for loop: 
```
for ($i = 0; $i < 10; $i++) {
  echo $i . "<br>";
}
```
- php while loop: 
```
$i = 0;
while ($i < 10) {
    echo $i . "<br>";
    $i++;
}
```
- php foreach loop: 
```
$colors = array("red", "green", "blue"); 
foreach ($colors as $color) {
  echo $color . "<br>";  
}
```
11. ip6 vs ip4
- ip6: 128 bits (192.0.2.1.), 8bits * 4
- ip4: 32 bits (2001:0db8:85a3:0000:0000:8a2e:0370:7334.), 16 bits * 8

12. Which range of http response status codes indicates successful responses? 200-299

13. HTML textarea
```
<label for="message">Message:</label>
<textarea id="message" name="message" rows="4" cols="40"> Enter your message here...</textarea>
```
14. form element collect data
```
<form action="submit.php" method="post">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name"><br>

  <label for="email">Email:</label>
  <input type="email" id="email" name="email"><br>

  <label for="message">Message:</label>
  <textarea id="message" name="message" rows="4" cols="40"></textarea><br>

  <input type="submit" value="Submit">
</form>
```

15. how to include js in html and php
```
<?php echo "<script>alert('Hello, world!');</script>"; ?>
```
```
<html>
  <head>
    <script src="myscript.js"></script>
  </head>
</html>
```

16. which attribute is mandatory to for img and which is optional
- src mandatory and alt is optional.

17. stylesheet which one will apply?
- the priority of a style rule is determined by the specificity of the selector used to apply the rule.
- specificity: Inline styles > ID selectors > class selectors > element selectors. 
- Universal selectors (*), combinators (+, >, ~), and pseudo-classes (:first-child, :hover, etc.) have a lower specificity than ID selectors, class selectors, or element selectors.
- If two or more selectors have the same specificity, the one that appears last in the stylesheet takes precedence.
- you should use specific selectors to target the elements you want to style.

18. rowspan--table?

```
<table>
  <tr>
    <th colspan="2">Name</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>Jill</td>
    <td>Smith</td>
    <td rowspan="2">30</td>
  </tr>
  <tr>
    <td>Eve</td>
    <td>Jackson</td>
  </tr>
</table>
```
<table>
  <tr>
    <th colspan="2">Name</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>Jill</td>
    <td>Smith</td>
    <td rowspan="2">30</td>
  </tr>
  <tr>
    <td>Eve</td>
    <td>Jackson</td>
  </tr>
</table>

19. inline vs block
- block elements are those that take up the full width of their parent container, and create a new line after themselves. Examples of block-level elements include 
div, p, h1
- inline elements are those that only take up as much width as their content requires, and do not create a new line after themselves. Examples of inline-level elements include span, a, img.


20. Elements that do not require a closing tag include:
- img and br self-closing.
- meta, link and other elements that do not define content.

21. DOM event 
```
<button id="myButton">Click me</button>

<script>
// Get a reference to the button element
var button = document.getElementById("myButton");

// Add an event listener to the button element
button.addEventListener("click", function(event) {
  console.log("Button clicked");
});

// Add another event listener to the button element
button.addEventListener("mouseover", function(event) {
  console.log("Mouse over button");
});
</script>
```

22. most common JS events
- click - This event is triggered when an element is clicked.
- mouseover - This event is triggered when the mouse pointer is moved over an element.
- keydown - This event is triggered when a key is pressed down.
- load - This event is triggered when a web page has finished loading.
- submit - This event is triggered when a form is submitted.
- change - This event is triggered when the value of an element changes, such as when a checkbox is checked or unchecked.
- keyup is an event that is triggered when the user releases a key on the keyboard. For example, when the user types something into a text field or other input element.

23. how to avoid the js error "cannot set property"? use defer or put js to the end 

24. isset() is the method to check if a variable is set in your script.

25. Which php function is used to decode a json string and return a php object by default? json_decode()

26. AJAX
- AJAX is a combination of several web technologies, including HTML, CSS, JavaScript, and XML (or JSON).
- AJAX allows web pages to update data dynamically without requiring a full page refresh.
- AJAX requests are typically initiated by JavaScript code running in the browser.
- AJAX requests are sent to the server using the XMLHttpRequest (XHR) object in JavaScript.
- AJAX can be used to fetch data from a server (e.g. a database), send data to a server (e.g. form data), or update a web page dynamically.
- AJAX responses can be in a variety of formats, including HTML, XML, JSON, and plain text.
- AJAX requests and responses are typically asynchronous, which means that they occur independently of the rest of the web page's code.
- AJAX can be used to create interactive and responsive web applications, such as web-based email clients, real-time chat applications, and online shopping carts.
- AJAX requires careful consideration of security issues, such as cross-site scripting (XSS) attacks and cross-site request forgery (CSRF) attacks.
- AJAX is widely used in modern web development and is an important tool for creating dynamic and interactive web pages.


