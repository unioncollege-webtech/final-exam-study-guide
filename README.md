# Final Exam Study Guide

The final exam in Web Technologies covers basic JavaScript language features as well as important <abbr title="HyperText Transfer Protocol">HTTP</abbr> topics such as methods, status codes, and headers.

* [JavaScript](#javascript)
* [HyperText Transfer Protocol](#hypertext-transfer-protocol)



## JavaScript

### Data Types

JavaScript has 6 primitive data types:

- **string** - a sequence of characters, `"Howdy"` or `'Howdy'`
- **number** - any numeric value, `42`, or `3.141592`
- **boolean** -  `true` and `false`
- **null** -  a special keyword denoting a `null` value
- **undefined** - a value automatically assigned to variables that don't yet have a value
- **symbol** - new in ECMAScript 6

And one complex data type:

- object - containers that have properties, and often methods, constructors, and prototypes

### Variable Declarations

The `var` keyword is used to declare a variable:

```
var counter;
```

A variable declaration can optionally initialize the variable with a value.

```
var counter = 0;
```

### Strings

A [string literal] is zero or more characters enclosed in double (") or single
(') quotation marks. There is no separate "char" type for individual characters.

```
var doubleQuoted = "This is a double-quoted string";
var singleQuoted = 'This uses single quotes';
var singleChar = 'a';
```

[string literal]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types#String_literals

### String Concatenation

The [Addition](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators#Addition)
(`+`) operator is used for string concatenation.

```
var hello = "Hello";
console.log( hello + " world" );
// => "Hello world"
```

###  String Properties and Methods

Strings have methods and properties defined on the 
[`String.prototype`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/prototype#Description) object:

- `.length`: A property which reflects the number of characters in the string
```
"hello".length // => 5
```

### Numbers

Numbers represent numeric values. Note that there is only *one* number type,
represented in [64-bit double-precision floating-point format](https://en.wikipedia.org/wiki/Double-precision_floating-point_format)

```
var answer = 42;
var pi = 3.14159;
```

### Arithmetic Operators

JavaScript defines several arithmetic operators which take numerical values (either literals or variables) as their operands and return a single numerical value.

- `+` Addition operator
  ```
  3 + 4 // => 7
  ```
- `-` Subtraction operator
  ```
  3 - 4 // => -1
  ```
- `*` Multiplication operator
  ```
  3 * 4 // => 12
  ```
- `/` Division operator
  ```
  3 / 4 // => 0.75
  ```
- `%` Remainder operator
  ```
  4 % 3 // => 1
  ```
### Assignment Operators

- `=` Assignment operator: assigns a value to its left operand based on the value of its right operand.
  ```
  var x = 10;     // The variable `x` now has the value `10`
  console.log(x);
  // => 10
  ```

- `+=` Addition assignment: adds the value of the right operand to a variable and 
  assigns the result to the variable
  ```
  var x = 10;
  x += 5;    // Equivalent to: x = x + 5
  ```

- `-=` Subtraction assignment
- `*=` Multiplication assignment
- `/=` Division assignment 
- `%=` Modulus assignment 

[Assignment operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment_Operators#Addition_assignment_2)
on MDN

### Increment Operators

- `++` Increment operator: increase a reference’s value by one and return the new value
  - Postfix: Return the original value **before** incrementing
    ```
    var a = 3;
    var b = a++;     // b: 3, a: 4
    ```
  - Prefix: Return the new (incremented) value
    ```
    var a = 3;
    var b = ++a;     // b: 4, a: 4
    ```

### Operators: Decrement

- `--` Decrement operator: decrease a reference’s value by one and return the new value
  - Postfix: Return the original value **before** decrementing
    ```
    var a = 3;
    var b = a--;     // b: 3, a: 2
    ```
  - Prefix: Return the new (decremented) value
    ```
    var a = 3;
    var b = --a;     // b: 2, a: 2
    ```

### Math

The global [`Math`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)
object has utilities for dealing with numbers.

- `Math.round(x)` : Returns the value of a number rounded to the nearest integer.

```
Math.round(3.14)   // =>  3
Math.round(1.618)  // =>  2
Math.round(-3.14)  // => -3
Math.round(-1.618) // => -2
```

### Booleans

Booleans represent one of two values: `true` or `false`. The keyword `true`
(lowercase) and `false` (lowercase) are the only two boolean types.

```
var answer = true;
var differentAnswer = false;
```

### Equality operators

- `==` Equality
- `===` Strict/identity equality
- `!=` Inequality
- `!==` Strict/identity inequality

[Equality operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators#Equality_operators)

### Equality operator

```js
x == y
```

The equality operator **converts** the operands if they are not of the same type, then applies strict comparison. 

```js
console.log(1 == 1);      // => true
console.log(1 == '1');    // => true
console.log(true == '1'); // => true
console.log(0 == 0);      // => true
console.log(0 == '0');    // => true
console.log(0 == '');     // => true
console.log(false == '0');// => true
var x = {};
var y = x;
console.log(x == y);       // => true
```

### Inequality operator

```js
x != y
```

The inequality operator **converts** operands if they are not of the same type, then returns true if the operands are **not** equal.

```js
console.log(1 != 1);      // => false
console.log(1 != '1');    // => false
console.log(true != '1'); // => false
console.log(1 != 0);      // => true
console.log('apples' != 'oranges'); // => true
var x = {};
var y = {};
console.log(x != y);      // => true
```

### Identity / strict equality operator

```js
x === y
```

The identity operator returns true if the operands are strictly equal (see above) with no type conversion.

```js
console.log(1 === 1);      // => true
console.log(1 === '1');    // => false
console.log(true === '1'); // => false
console.log(0 === 0);      // => true
console.log(0 === '0');    // => false
console.log(0 === '');     // => false
console.log(false === '0');// => false
var x = {};
var y = x;
console.log(x === y);       // => true
```

### Identity / strict inequality operator

```js
x !== y
```

The non-identity operator returns true if the operands are not equal and/or not of the same type.

```js
console.log(1 !== '1') // true
console.log(1 !== 2)   // true
```

### Relational operators

- `>` Greater than
  ```
  3 > 4 // => false
  4 > 4 // => false
  5 > 4 // => true
  ```
- `>=` Greater than or equal
  ```
  3 >= 4 // => false
  4 >= 4 // => true
  5 >= 4 // => true
  ```
- `<` Less than operator
  ```
  3 < 4 // => true
  4 < 4 // => false
  5 < 4 // => false
  ```
- `<=` Less than or equal
  ```
  3 <= 4 // => true
  4 <= 4 // => true
  5 <= 4 // => false
  ```

[Relational operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators#Relational_operators)

### If statement

```js
if (condition)
   statement1
else               // optional `else`
   statement2
```

Executes `statement1` if a `condition` is true. If `condition` is false, statement2 is executed.

[if...else statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)

### Conditional (ternary) operator

```js
condition ? expression1 : expression2
```

Return `expression1` if `condition` is true, otherwise return `expression2`

[Conditional (ternary) operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)

### Logical operators

- `&&` &nbsp; Logical AND
- `||` &nbsp; Logical OR
- `!` &nbsp; &nbsp; Logical NOT

[Logical operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators)

### Truthiness

JavaScript coerces primitives and objects to a Boolean when a Boolean is expected.

#### Falsy

The following 6 values are considered `false` in a boolean context:

- `false` 
- `0`
- `''` (empty string)
- `null`
- `undefined`
- `NaN`

#### Truthy

A value is “truthy” if it is not “falsy.” 

The following values (among many others) are considered `true` in a boolean context:

- `true`
- `"hi"`
- `12`
- `-1`
- [] (empty array)
- {} (empty object)

### `for` loops

Syntax:

```
for ([initialization]; [condition]; [final-expression])
   statement
```

```
// Log the numbers 1 through 10
for (var i = 1; i <= 10; i++) {
   console.log( i );
}
```

[`for` reference on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for)

### `for` loops: Arrays

A common use case for `for` loops is looping through array values:

```
var scores = [89, 98, 92, 69, 87, 53];
for (var i = 0; i < scores.length; i++) {
   console.log( scores[i] );
}
```

### Arrays

An array is an ordered set of numerically-indexed values.

Arrays can be created using the global `Array` function (not recommended) or by
using the [Array literal](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types#Array_literals): `[]`

```
var empty = [];
var scores = [88, 75, 84, 100, 77, 105, 86];
var books = ["To Kill a Mockingbird", "Prince Caspian", "The Hitchhiker’s Guide to the Galaxy"]
```

Array values can accessed or assigned by a numeric index

```
console.log( books[0] );  // => "To Kill a Mockingbird"
books[0] = "Fellowship of the Ring";
console.log( books[0] );  // => "Fellowship of the Ring"
```

[Introduction to Arrays on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Indexed_collections)

#### Array methods: push

`push()` adds one or more elements to the end of an array and returns the resulting length of the array.

```
var myArray = ["1", "2"]
myArray.push("3"); // myArray is now ["1", "2", "3"]
```

#### Array methods: sort

`sort([sortFunction])` sorts the elements of an array.

```
var myArray = ["Wind", "Rain", "Fire"];
myArray.sort(); 
// sorts the array so that myArray = [ "Fire", "Rain", "Wind" ]
```

`sort()` can also take a callback function to determine how array elements are 
compared. The function compares two values and returns one of three values:

- if a is **less than** b by the sorting system, return `-1` (or any negative 
  number)
- if a is **greater than** b by the sorting system, return `1` (or any positive
  number)
- if a and b are considered **equivalent**, return `0`.

For instance, the following will sort by the last letter of a string:

```
var sortFn = function(a, b){
  if (a[a.length - 1] < b[b.length - 1]) return -1;
  if (a[a.length - 1] > b[b.length - 1]) return 1;
  if (a[a.length - 1] == b[b.length - 1]) return 0;
}
myArray.sort(sortFn); 
// sorts the array so that myArray = ["Wind","Fire","Rain"]
```

#### Array methods: indexOf

`indexOf(searchElement[, fromIndex])` searches the array for `searchElement` and
returns the index of the first match.

```
var a = ['a', 'b', 'a', 'b', 'a'];
console.log(a.indexOf('b')); // logs 1
// Now try again, starting from after the last match
console.log(a.indexOf('b', 2)); // logs 3
console.log(a.indexOf('z')); // logs -1, because 'z' was not found
```

### Array methods: forEach

`forEach(callback[, thisObject])` executes `callback` on every array item.

```
var a = ['a', 'b', 'c'];
// log each item in the array
a.forEach(function(element) {
  console.log(element);
}); 
```

#### Array methods: map

`map(callback[, thisObject])` returns a new array of the return value from 
executing `callback` on every array item.

```
var a1 = ['a', 'b', 'c'];
var a2 = a1.map(function(item) { return item.toUpperCase(); });
console.log(a2); // logs A,B,C
```

#### Array methods: filter

`filter(callback[, thisObject])` returns a new array containing the items for 
which `callback` returned `true`.

```
var a1 = ['a', 10, 'b', 20, 'c', 30];
var a2 = a1.filter(function(item) {
  return typeof item == 'number';
});
console.log(a2); // logs 10,20,30
```

### Objects

Objects are lists of values similar to arrays, except values are identified by keys instead of integers.

Here is an example:

```
var foodPreferences = {
  pizza: 'yum',
  salad: 'gross'
};
```

You can access and manipulate object properties –– the keys and values that an object contains –– using a method very similar to arrays.

```
console.log(foodPreferences['pizza']);
```

The above code will print the string `'yum'` to the terminal.

Alternately, you can use **dot notation** to get identical results:

```
foodPreferences.pizza;

foodPreferences['pizza'];
```

The two lines of code above will both return `yummy`.

### Functions

A function is a block of code that takes input, processes that input, and then produces output.

```
function example (x) {
  return x * 2;
}
```

We can **call** that function like this to get the number 10:

```
example(5);
```

### Function Arguments

A function can be declared to receive any number of arguments. Arguments can be from any type. An argument could be a string, a number, an array, an object and even another function.

```js
function example (firstArg, secondArg) {
  console.log(firstArg, secondArg);
}
```

We can **call** that function with two arguments like this:

```js
example('hello', 'world');
```

### Methods

A function that is a property of an object is known as a **method**. Methods can refer to their parent object by using the keyword `this`.

```
var student = {
  name: "Ben",
  speak: function() {
    console.log(this.name);
  }
};

student.speak();
// => "Ben"
```

### Constructors

// TODO

### Prototype

// TODO

---

## HyperText Transfer Protocol

<abbr title="HyperText Transfer Protocol">HTTP</abbr> is an *application level* protocol for communication between a user-agent (typically a browser) and a server. From the [HTTP 1.1 Specification](http://www.w3.org/Protocols/rfc2616/rfc2616-sec1.html#sec1.4):

> The HTTP protocol is a request/response protocol. A client sends a request to the server in the form of a [request method](#http-methods), URI, and protocol version, followed by a MIME-like message containing request modifiers, client information, and possible body content over a connection with a server. The server responds with a status line, including the message's protocol version and a [success or error code](#http-status-codes), followed by a MIME-like message containing server information, entity metainformation, and possible entity-body content.


### HTTP Methods

HTTP defines several **Methods** which indicate the action to take for the specified resource. See the [Method Definitions](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9) in the HTTP 1.1 specification.

#### [OPTIONS](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.2)

The OPTIONS method represents a request for information about the communication options available on the request/response chain identified by the Request-URI. This method allows the client to determine the options and/or requirements associated with a resource, or the capabilities of a server, without implying a resource action or initiating a resource retrieval.

#### [GET](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.3)

The GET method means retrieve whatever information (in the form of an entity) is identified by the Request-URI.

#### [HEAD](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.4)

The HEAD method is identical to GET except that the server MUST NOT return a message-body in the response. 

The metainformation contained in the HTTP headers in response to a HEAD request SHOULD be identical to the information sent in response to a GET request. This method can be used for obtaining metainformation about the entity implied by the request without transferring the entity-body itself. This method is often used for testing hypertext links for validity, accessibility, and recent modification.

#### [POST](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.5)

The POST method is used to request that the origin server accept the entity enclosed in the request as a new subordinate of the resource identified by the Request-URI. POST was originally designed to allow a uniform method to cover the following common functions:

- Posting a message to a bulletin board, newsgroup, mailing list, or similar group of articles;
- Providing a block of data, such as the result of submitting a form, to a data-handling process;
- Annotating or altering existing resources.

#### [PUT](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.5)

The PUT method requests that the enclosed entity be stored under the supplied Request-URI.

#### [DELETE](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.7)

The DELETE method requests that the origin server delete the resource identified by the Request-URI.

#### [PATCH](http://tools.ietf.org/html/rfc5789#section-2)

Specified in [RFC 5789](http://tools.ietf.org/html/rfc5789), the PATCH method requests that a set of changes described in the request entity be applied to the resource identified by the Request-URI.

#### Safe and Idempotent Methods

##### Safe Methods

GET and HEAD methods are considered "safe", meaning they SHOULD NOT have the significance of taking an action other than retrieval. GET and HEAD requests should not alter the resource being requested.

##### Idempotent Methods

The methods GET, HEAD, PUT and DELETE are considered "idempotent", meaning multiple identical requests for the same resource should have the same side-effects as a single request for that resource. POST methods are NOT expected to be idempotent.


### [HTTP Status Codes](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10)

HTTP statuses indicate the result of the attempt to understand and satisfy the request. The status consists of a Status-Code and a short textual description known as the Reason-Phrase. The Status-Code is a 3-digit integer. The first digit of the Status-Code defines the class of response. The last two digits do not have any categorization role. There are 5 values for the first digit:

- 1xx: Informational - Request received, continuing process
- 2xx: Success - The action was successfully received,
  understood, and accepted
- 3xx: Redirection - Further action must be taken in order to
  complete the request
- 4xx: Client Error - The request contains bad syntax or cannot
  be fulfilled
- 5xx: Server Error - The server failed to fulfill an apparently
  valid request

#### [100 Continue](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.1.1)

The client SHOULD continue with its request. This interim response is used to inform the client that the initial part of the request has been received and has not yet been rejected by the server. The client SHOULD continue by sending the remainder of the request or, if the request has already been completed, ignore this response. 

#### [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1)

The request has succeeded. The information returned with the response is dependent on the method used in the request

#### [301 Moved Permanently](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.3.2)

The requested resource has been assigned a new permanent URI (identified by the Location field in the response) and any future references to this resource should use the new URI. This response is cacheable unless indicated otherwise.

#### [302 Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.3.2)

The requested resource resides temporarily under a different URI. Since the redirection might be altered on occasion, the client SHOULD continue to use the Request-URI for future requests. This response is only cacheable if indicated by a Cache-Control or Expires header field.

#### [304 Not Modified](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.3.5)

If the client has performed a conditional GET request and access is allowed, but the document has not been modified, the server SHOULD respond with this status code. The 304 response MUST NOT contain a message-body, and thus is always terminated by the first empty line after the header fields.

#### [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1)

The request could not be understood by the server due to malformed syntax. The client SHOULD NOT repeat the request without modifications.

#### [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2)

The request requires user authentication.

#### [403 Forbidden](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.4)

The server understood the request, but is refusing to fulfill it. Authorization will not help and the request SHOULD NOT be repeated.

#### [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5)

The server has not found anything matching the Request-URI. No indication is given of whether the condition is temporary or permanent.

#### [410 Gone](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.11)

The requested resource is no longer available at the server and no forwarding address is known. This condition is expected to be considered permanent.

#### [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1)

The server encountered an unexpected condition which prevented it from fulfilling the request.

#### [503 Service Unavailable](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.4)

The server is currently unable to handle the request due to a temporary overloading or maintenance of the server. 


### Message Headers

[HTTP header fields](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14) consist of a name followed by a colon (":") and the field value. There are four different categories of header fields:

- **general**: have general applicability for both request and response messages, but which do not apply to the entity being transferred
- **request**: allow the client to pass additional information about the request, and about the client itself, to the server. These fields act as request modifiers, with semantics equivalent to the parameters on a programming language method invocation.
- **response**: allow the server to pass additional information about the response which cannot be placed in the Status- Line. These header fields give information about the server and about further access to the resource identified by the Request-URI.
- **entity**: define metainformation about the entity-body or, if no body is present, about the resource identified by the request.

