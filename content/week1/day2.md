+++
date = "2017-05-16T10:06:46-04:00"
title = "Day 2: Functions and Objects"
toc = true
next="/week1/day3"
prev="/week1/day1"
weight = 2

+++

<date>Tuesday, May 16, 2017</date>

## Lecture Videos

Morning:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [part 1](https://www.youtube.com/watch?v=wISoJ_P7aNs&t=10s&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=1) | [part 2](https://www.youtube.com/watch?v=6JkRe4ZLhGQ&index=2&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [part 3](https://www.youtube.com/watch?v=YQrKjzVOuxs&index=3&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F)

Afternoon:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [part 1](https://www.youtube.com/watch?v=Lz9SD8oDm3M&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=1) | [part 2](https://www.youtube.com/watch?v=kmLCIy6reuk&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=2) | [part 3](https://www.youtube.com/watch?v=T-JKi6NUxG8&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=3)

## Topics

### Functions
* Function Expressions
* Function Declarations
* Functions as Object properties (methods)
* Variable Scope (`var`, `const`, `let`)

### Objects
* Object literals
* Property Naming
* Retrieving property values
* Setting property values

### Arrays
* `Array.from` - [Docs on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from?v=control)
* `Array.map` - [Docs on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map?v=control) | [Understanding JavaScript's `map()`](https://www.discovermeteor.com/blog/understanding-javascript-map/) blog post

### DOM
* Creating elements with `document.createElement`
* Setting style properties with `someElement.style.stylePropertyName`
* Appending child elements with `someElement.appendChild`
* [Form.elements](https://developer.mozilla.org/en-US/docs/Web/API/HTMLFormElement/elements)

### Git and GitHub
* [Git - The Simple Guide](http://rogerdudler.github.io/git-guide/)
* [Getting your project on GitHub](https://guides.github.com/introduction/getting-your-project-on-github/)

## Examples

### Functions
{{< code js >}}
  // function declaration - use 'function' keyword
  function aMostExcellentFunction() {
    console.log('This function is great!')
  }

  aMostExcellentFunction() // => 'This function is great!'

  // function expression - defines a function as part of a larger expression syntax
  // (usually assignment to a variable)
  const anotherExcellentFunction = () => {
    console.log('This function is also great!')
  }

  anotherExcellentFunction() // => 'This function is also great!'

  // functions as object properties (also known as 'methods')
  const myObject = {
    myMethod() {
      console.log('I am a method!')
    }
  }

  myObject.myMethod() // => 'I am a method!'
{{< /code >}}

### Variable Scope
The biggest difference between `var` and `let` is that `var` variables are scoped to the _function_ in which they are declared, while `let` variables are scoped to the _block_ in which they are declared.  One of the easiest examples to see this behavior is in a simple `for` loop.

{{< code js >}}
function loopStuff() {
  for (var i = 0; i < 5; i++) {
    // do stuff in the loop
  }
  console.log(i)
}

loopStuff() // => 5

function loopMoreStuff() {
  for (let i = 0; i < 5; i++) {
    // do stuff in the loop
  }
  console.log(i)
}

loopMoreStuff() // => Uncaught ReferenceError: i is not defined
{{< /code >}}

In the function `loopStuff`, `var i` is still available outside the `for` loop so it can be logged to the console.  It is scoped to the function itself.

In the function `loopMoreStuff`, `let i` is not available outside the block it is scoped to (the `for` loop).

The main difference between `const` and `var`/`let` is that `const` cannot be reassigned.
{{< code js >}}
let variableOne = 4
variableOne = 5

var variableTwo = 4
variableTwo = 5

const variableThree = 4
variableThree = 5 // => Uncaught TypeError: Assignment to constant variable
{{< /code >}}

{{% aside tip "Default to using const" %}}
Always use `const` as your default way to declare variables, unless you know specifically that you will need to reassign it, in which case use `let`.  You should rarely, if ever, use `var`.  For further reading, check out [this article](https://medium.com/javascript-scene/javascript-es6-var-let-or-const-ba58b8dcde75)
{{% /aside %}}

### Objects
Almost everything in JavaScript is an Object.  The easiest way to create new Objects is with the [object initializer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer), more commonly known as 'object literal' syntax.  Basically, use curly braces to make an object `{}` and fill in the properties that you want.

Objects contain `key`/`value` pairs that allow you to set and retrieve values from them.

{{< code js >}}
// create a new object and assign some properties
const myObject = {
  prop1: 'Hello there',
  prop2: 42
}

// access the values in several ways, usually 'dot' or 'square bracket' notation
myObject.prop1 // => 'Hello there'
myObject['prop1'] //=> 'Hello there'

// new key/value pairs can also be assigned with these notations
myObject.prop3 = 'New Value!'
myObject['prop4'] = 'Newest Value!'

console.log(myObject)
// { 
//   prop1: 'Hello there',
//   prop2: 42,
//   prop3: 'New Value!',
//   prop4: 'Newest Value!'
// }
{{< /code >}}

### Arrays
Arrays are extremely useful data structures in JavaScript, as they can be easily iterated and transformed through methods like `map`, `filter`, and `reduce`.  Sometimes, you may have an 'array-like' collection (like a `NodeList` or function arguments) that you would need to convert to an actual Array before you could use these methods.  This can be done using `Array.from`

{{< code js >}}
let paragraphs = document.querySelectorAll('p')
paragraphs.map((paragraph) => {
  p.textContent = "This won't work because paragraphs is a NodeList, not Array!"
})
// => Uncaught TypeError: paragraphs.map is not a function

let actualArrayOfParagraphs = Array.from(paragraphs)
actualArrayOfParagraphs.map((paragraph) => {
  p.textContent = "This totally does work because we created an Array from our NodeList!"
})
{{< /code >}}

{{% aside info "Requirements for 'Array.from'" %}}
What objects can you convert to an Array using 'Array.from'?  

* Any array-like object with a 'length' property and indexed elements
* Iterable objects (like Map or Set)

For more info, check out [this article](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from?v=control) on MDN.
{{% /aside %}}

### DOM
If we start with the following markup:
{{< code html >}}
&lt;div id=&quot;my-div&quot;&gt;&lt;/div&gt;
{{< /code >}}
We can add additional markup to it programmatically using JavaScript.  One way is to create new HTMl elements using `document.createElement`, and adding them by using `appendChild`.  Styling of the element can even be changed by manipulating the element's `style` property.

{{< code js >}}
// create an h1 and modify text content and color
const heading = document.createElement('h1')
heading.textContent = "This is the best heading I've ever seen"
heading.style.color = "red"

// get a reference to the existing div and add the heading as a child element
const div = document.querySelector('#my-div')
div.appendChild(heading)
{{< /code >}}

This will produce the following markup:
{{< code html >}}
&lt;div id=&quot;my-div&quot;&gt;
  &lt;h1 style=&quot;color: red;&quot;&gt;This is the best heading I've ever seen&lt;/h1&gt;
&lt;/div&gt;
{{< /code >}}

## Presentations

* [Review: HTML and the DOM](/02-html-dom.pdf)

## Projects

### People Factory
[Morning](https://github.com/xtbc17s1/people-factory) | [Afternoon](https://github.com/xtbc17s1/people-factory/tree/afternoon)

## Homework
### Megaroster

Create a new project from scratch that adds students to a class roster and meets the following requirements:

#### Baseline Goal

* User can enter a name to be added to the roster.
* Name will be added to the end of a list.

#### Bonus Credit

* Create _at most_ one global variable.

#### Mega Bonus Credit

* Add names to the top of the list instead of the bottom.

#### Super Mega Bonus Credit

* Add a _delete_ button to every list item that removes the name from the list when clicked.

#### Super Mega Bonus Credit Hyper Fighting

* Add a _promote_ button to every list item that changes the appearance(_e.g._ changes the background color, adds a border, etc.) of that item when clicked.



