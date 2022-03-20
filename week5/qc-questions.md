## HTML-CSS QC Questions

1. What is HTML

   - HTML stands for Hypertext Markup Language and consists of various tags to describe the content of a document - utilized as the basis for all web pages, along with CSS and JavaScript

2. What is the structure of an HTML document? List some tags. What is `<head>` used for? `<body>`?

   - Start with the doctype declaration, then `<html>`, then `<head>` and `<body>`. The head contains the metadata for the page, while the body contains the content that is rendered to the screen. Other tags: div, span, p, ul, ol, li, strong, em, table

3. What is a doctype?

   - First tag in the document - defines what type of file it is - whether html 4 or 5, etc

4. What is the tag for an ordered list? Unordered list?
   - ordered list: ol, unordered list: ul. Both use li - list items
5. What are some HTML5 tags? Why were HTML5 tags introduced?

   - HTML5 introduced semantic tags to more accurately reflect the content of the tags. Examples: `<strong>` instead of `<b>`, `<em>` instead of `<i>`, `<nav>`, `<header>`, `<footer>`, `<section>`, `<article>`, and `<aside>` instead of reusing `<div>` tags everywhere

6. Do all tags come in a pair? What are the other things inside tags called? list some.

   - No - tags either have a closing tag or are self-closing (`<tag />`). Attributes are contained within tags - examples: id, class, style, height, width, etc

7. What is the syntax for a comment in HTML?

   - `<!-- comments go in here -->`

8. Give me the HTML markup for a table.

```html
<table>
  <caption>
    optional
  </caption>
  <thead>
    <tr>
      <td>Heading 1</td>
      <td>Heading 2</td>
    </tr>
  </thead>
  <tr>
    <td>Cell 1</td>
    <td>Cell 2</td>
  </tr>
  <tbody></tbody>
</table>
```

9. What are some tags you would use in a form?

   - Form tags: `<form>`, `<input>`, `<label>`, `<textarea>`, `<button>`, `<select>`, `<option>`

10. What is CSS? what are the different ways of styling an HTML file? Which is best? why?

    - CSS stands for Cascading Style Sheets - it is a language for styling HTML documents by specifying certain rules for layout and display in key/value pairs. There are 3 ways of styling an HTML file:
    - (1) inline - in the `style` attribute
    - (2) internal stylesheet - in the `<style>` tag in the `<head>`
    - (3) external stylesheet - using external `.css` file, use `<link>` in the `<head>`
    - External stylesheet is best practice due to separation of concerns, reusability, modularity

11. Describe the CSS box model.

    - The box model consists of margin (outermost box), then border, then padding, then content (innermost). All box sizes / formatting can be styled with CSS

12. Which way has highest priority when styles cascade: inline, internal, and external.

    - Inline has highest priority, then internal/external depending on order. Cascading rules are determined by (1) importance (`!important` flag), (2) specificity of selector (inline has no selector, highest specificity), then (3) source order.

13. Syntax for styling an element? What is a class and how to style them? What is an id? how to style? difference?

```css
div {
  property: value;
}
.class {
  property: value;
}
#id {
  property: value;
}
```

14. What if I want to select child elements, What syntax is that?

    - use direct descendant selector (`>`) or space for any level nested element

15. Can I select multiple elements at once? How?

    - yes, with a comma

## JavaScript

### Basic

- What is JavaScript? What do we use it for?

- Can we run JavaScript in a web browser, on a server, or both?

- What are the benefits of JS over your core language? Drawbacks?

- What programming paradigm(s) does JS support?

- What are the data types in JS?

  - What is the type of NaN? What is the isNaN function?

  - What is the data type of a function?

  - What about an array?

  - What is the difference between undefined and null?

- What are JS objects? what is the syntax?

- Use the object literal syntax to create an object with some properties

- What are arrays in JS? can you change their size?

- List some array methods and explain how they work.

- What is JSON? Is it different from JS objects?

- What are some ways you can use functions in JS?

- What are the different scopes of variables in JS?

  - What are the different ways to declare global variables?

  - Is it a best practice to use global variables? Why or why not?

- What are some methods on the function prototype?

- If you declare a variable `var` inside a for loop is that block scoped or function scoped?

  - If you declare a variable `let` inside a for loop is that block scoped or function scoped?

- What will happen?

```javascript
const hi;
hi = 3;
console.log(hi);
```

- What are callback functions? What about self-invoking functions?

- What is a truthy or falsy value? List the falsy values.

- What prints?:

```javascript
let x = 5;
while (x) {
  x--;
  console.log(x);
}
```

- What is the difference between == and ===? Which one allows for type coercion?

- What is the difference between `for of` and `for in`?

- What does the following code do?

```javascript
function addOne(value) {
  value + 1;
}

let x = 5;
addOne(x);
console.log(x);
```

What about this?

```javascript
function changeUsername(user) {
  user.username = "new-username";
}

let user = {
  username: "first-username",
};

changeUsername(user);
console.log(user.username);
```

Why?

- What is the difference between a do-while and a while loop?

- What does this do?

```javascript
for (;;) {
  console.log("a");
}
```

- What is fall-through with regard to switch statements?

- What is the difference between `console.log(++x)` and `console.log(x++)`?

- Explain what “strict mode” does

- What are the naming conventions for a variable used in JavaScript?

- What are the naming conventions for a function used in JavaScript?

### Intermediate

- What is function and variable hoisting?

- What is closure and when should you use it?

- What does the following code do?

```javascript
let arr = [1, 2, 3, 4];
let x = arr.forEach(function (x) {
  return x * x;
});
console.log(x);
```

_prints_: undefined

- What does the following code do?

```javascript
let arr = [1, 2, 3, 4];
let x = arr.map(function (x) {
  return x * x;
});
console.log(x);
```

_prints_ [1, 4, 9, 16]

- What does the "this" keyword refer to?

- Explain the concept of lexical scope

- Explain how inheritance works in JS

- How would you rewrite this using an anonymous function? Arrow function?

```JavaScript
function hello(){
  console.log('hello');
}
document.getElementById('hi').addEventListener(hello);
```

- What is the difference between `setInterval()` and `setTimeout()`?

  - How would you stop a `setInterval()` once it has been set?
  - Advanced: How do they work with regards to the callback queue?

- How would you handle an error in JS?

- What attributes does an Error object have?

- What is an Immediately Invoked Function Expression?
  - How would you write one?

### Advanced

- What are some characteristics of the functional programming paradigms

- What does it mean for a function to have no side effects? (what is a pure function?)

- What are the advantages to using a functional approach? (as opposed to OOP)

- Explain how the guard and default operators work

- What happens:

```JavaScript
let h = 'hello';
function process(input) {
  return input || 'goodbye';
}
console.log(process(h));
console.log(process());
```

### Bonus

- What will happen when I try to run this code: console.log(0.1+0.2==0.3) ?

- What happens?

```javascript
h = 3;
function hello() {
  h = 6;
}
hello();
console.log(h);
```

- What prints?

```javascript
let x = 5;
let b = 2;
for (let i = 0; i < 5; i++) {
  b = b + 1;
}
if ((b = x)) {
  console.log(b);
} else {
  console.log("Oh no. :(");
}
```

## ES6+

### Basic

- What standard is JS based off of?

- What is the difference between var, let, and const keywords?
- How would we rewrite this code with a template literal?

```JavaScript
let n = 'Dorian';
let message = 'My name is '+n;
console.log(message);
```

- What will print:

```JavaScript
let arr = ['chicken', 'pig', 'cow'];
for(let i in arr) {
  console.log(i);
}
for(let i of arr) {
  console.log(i);
}
```

- What will happen:

```JavaScript
let arr = ['chicken', 'pig', 'cow'];
for(const i in arr) {
  console.log(i);
}
```

### Intermediate

- What’s the difference between a normal function declaration and an arrow function?
- Does JS have classes? How does this relate to Prototypal inheritance in JS/What is the difference between a Prototype and a Class?
- How would you set default values for parameters to a function?
- What’s the benefit of computed property names?
- Explain the async/await keywords. Why is it preferred to use this instead of .then() methods?

- How could you make the program print out the statements in order?

```JavaScript
function getData(){
  console.log("2. Getting data from internet, please wait.")
  return setTimeout(function(){
    console.log("3. Returning data from internet after 1000 milliseconds.")
    return [{name: "Avi"}, {name: "Grace"}]
  }, 1000)
}

function main(){
  console.log("1. Starting Script")
  const data = getData()
  console.log(`4. Data is currently ${data}`)
  console.log("5. Script Ended")
}

main();
```

Solution:

```JavaScript
function getData(){
  console.log("2. Getting data from internet, please wait.")
  return new Promise(function(resolve){
    setTimeout(function(){
      console.log("3. Returning data from internet.")
      resolve([{name: "Avi"}, {name: "Grace"}])
    }, 1000)
  })
}

async function main(){
  console.log("1. Starting Script")
  const data = await getData()
  console.log(`4. Data is currently ${JSON.stringify(data)}`)
  console.log("5. Script Ended")
}

main()
```

- How do you interact with a Promise? When would it be appropriate to use a Promise?

- Write a method that would print to the console the value returned by the promise?

```JavaScript
function helloPromise() {
  let p = new Promise();

  setTimeout(p.resolve(`Hello World`), 500);

  return p;
}
```

Solution:

```JavaScript
helloPromise().then(r -> console.log(r));
```

- Convert this function to use named parameters?

```JavaScript
function add(x, y) {
  return x + y;
}
```

Solution:

```JavaScript
function add(options) {
  return options.x + options.y;
}
```

### Advanced

- What is a Symbol? What is the advantage using Symbol?

- How could you reference this module in your code?

```JavaScript

export const qcScore = `RED`;

```

Solution:

```JavaScript

import {qcScore} from './filenameTheyShouldAskForFromQC.js';

```

- What is object and array destructuring? Give me an example using the rest/spread operator?

- What is a generator function? What’s the point of the yield keyword?
- What built-in advanced objects does JavaScript provide?

- What will this print?

```JavaScript

let fname = "Bobbert";
let lname = "Bobbertson";
let role = "manager";
let status = "active";

let user = {
  fname,
  lname,
  [role]: status,
  fullname: () => `${fname} ${lname}`
};

console.log(user);

console.log(user.fullname());

```

## DOM Manipulation

- Explain the following code:

```javascript
document.getElementById("myid").addEventListener("click", (e) => {
  e.stopPropagation();
});
```

- What is the global object in client-side JavaScript? What are some built-in functions on this object?

**example answers**: `window` is the correct answer (document is a field on the window object), but `document` is also acceptable.

- What is the DOM? How is it represented as a data structure? What object in a browser environment allows us to interact with the DOM?

- List some ways of querying the DOM for elements

- How would you insert a new element into the DOM?

- What are event listeners? What are some events we can listen for? What are some different ways of setting event listeners?

- What is bubbling and capturing and what is the difference?

- What are some methods on the event object and what do they do?

- Why is `Hello` not visible on the page after calling this function?

```JavaScript
function addElementToBody() {
  let body = document.getElementsByTagName('body');
  body.innerHTML = '<p>Hello</p>';
}
```

**answer:** You can't append a child to an `htmlCollection`.

### Bonus

- What happens?

```javascript
location = "www.google.com";
console.log(location);
```

## Asynchronous Web

- What is AJAX? why do we use it? What are the benefits of using AJAX? Are there any downsides of using AJAX?

- Explain why it is important that AJAX is asynchronous

- List the steps to sending an AJAX request

- What are steps to sending an AJAX request?

- List the different ready states of the XmlHttpRequest object

- How would retrieve JSON data from an AJAX request?

- How do you handle a failed request in AJAX?

- What is the Fetch API?

- How do you send a Fetch request?

- What is the difference between Fetch and AJAX?

- How would you retreive JSON data from a Fetch request?

- How do you handle a failed request in Fetch?

### Bonus

- How would you retrieve XML data from an xhr object?
