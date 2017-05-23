+++
date = "2017-05-15T11:13:46-04:00"
title = "Day 6: React"
prev="/week2/day5/"
toc = true
weight = 2

+++

<date>Tuesday, May 23, 2017</date>

## Lecture Videos

Morning:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [Day 6, part 1]() | [2]() | [3]() | [4]() | [5]() | [6]() | [7]() | [8]()

Afternoon:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [Day 6, part 1]() | [2]() | [3]() | [4]() | [5]() | [6]() | [7]() | [8]()

## Topics

### [React](https://facebook.github.io/react/)

* Using `map` with components
* Stateless Functional Components
* Conditional rendering
* Property initializers

### JavaScript

* Named and default exports
* Named and default imports

## Examples

### React

#### Using `map` with Components

**[See this example live on CodePen →](https://codepen.io/dstrus/pen/gWZVOQ?editors=0010#0)**

**Person.js**

{{< code jsx >}}
class Person extends React.Component {
  render() {
    return (
      &lt;li&gt;Hello, {this.props.person.name}!&lt;/li&gt;
    )
  }
}

export default Person
{{< /code >}}

**PersonList.js**

{{< code jsx >}}
import Person from './Person'

class PersonList extends React.Component {
  render() {
    const people = [
      { name: 'Seth', hair: 'blonde' },
      { name: 'Davey', hair: 'long gone' }
    ]
    return (
      &lt;div&gt;
        &lt;h2&gt;People&lt;/h2&gt;
        {
          people.map((person => &lt;Person person={person} /&gt;))
        }
      &lt;/div&gt;
    )
  }
}

export default PersonList
{{< /code >}}

#### Stateless Functional Components

Not every React Component needs to have state.  Many simply render a bit of `props` and UI.  For such components, we don't need to instantiate a whole class that inherits from `React.Component`, we can simply write a function that accepts `props` as an argument and returns the markup we need.

For instance, in the previous example, the `Person` component can easily be re-written as a Stateless Functional Component.

{{< code jsx >}}
function Person (props) {
  return (
    &lt;li&gt;Hello, {props.person.name}!&lt;/li&gt;
  )
}

// Or...

const Person = (props) => &lt;li&gt;Hello, {props.person.name}!&lt;/li&gt;
{{< /code >}}

#### Conditional Rendering

There are many instances where you may want to render different UI depending on the state of the application.  One example would be a button that shows "Log in" or "Log out", depending on whether there is a currently logged-in user.

Since React is just JavaScript, we can conditionally render using `if`/`else` statements, or we also learned about the [*ternary operator*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator).

{{< code js >}}
const condition = true

if (condition) {
  console.log('true!')
} else {
  console.log('false!')
}
// => 'true!'

condition ? console.log('true!') : console.log('false!')
// => 'true!'
{{< /code >}}

An example in React:

{{< code jsx >}}
function UserButton (props) {
  return (
    {props.loggedInUser ? &lt;button&gt;Log out&lt;/button&gt; : &lt;button&gt;Log in&lt;/button&gt;}
  )
}
{{< /code >}}

#### Property initializers

From the proposal:

> "Class instance fields" describe properties intended to exist on instances of a class (and may optionally include initializer expressions for said properties).

We can take advantage of this in a couple of ways.

[**Read more: Using ES7 property initializers in React**](https://babeljs.io/blog/2015/06/07/react-on-es6-plus)

We can use a property initializer to set the initial value of state without writing a constructor:

{{< code jsx >}}
class Song extends React.Component {
  state = {
    versesRemaining: 5,
  }
}
{{< /code >}}

We can even set default props and use those in the initial state:

{{< code jsx >}}
class Song extends React.Component {
  static defaultProps = {
    autoPlay: false,
    verseCount: 10,
  }
  state = {
    versesRemaining: this.props.verseCount,
  }
}
{{< /code >}}

Combining property initializers and arrow functions also gives us a convenient way to auto-bind `this`:

{{< code jsx >}}
class Something extends React.Component {
  handleButtonClick = (ev) => {
    // `this` is bound correctly!
    this.setState({ buttonWasClicked: true });
  }
}
{{< /code >}}

{{% aside danger "Subject to  minor changes" %}}
[Property initializers](https://github.com/tc39/proposal-class-public-fields) are a [Stage 2 proposal](https://tc39.github.io/process-document/) for ECMAScript, meaning that it's still a _draft_ and is subject to minor changes before becoming standardized. Facebook itself is already using these techniques in production, however.
{{% /aside %}}

### JavaScript (ES6+)

#### Named and default exports and imports

Prior to ES6, there were many competing ways to export and import JavaScript modules.  The most common were [CommonJS](https://webpack.github.io/docs/commonjs.html) and [AMD](http://requirejs.org/docs/whyamd.html).  Luckily ES6 defined a specification for standardizing module export and import.

There are two types of exports from any JS file - *named* and *default*.  The important thing to remember is that there can only be *one* default export per module, but there can be as many named exports as you want.

**myModule.js**
{{< code js >}}
export const myNumber = 8

export function sayHi () {
  console.log('hello')
}

export default class MyClass {
  add (a, b) {
    return a + b
  }
}
{{< /code >}}

The main difference is how they are imported.  Default exports get the most concise syntax:

{{< code js >}}
import MyClass from 'myModule'

const classInstance = new MyClass()
classInstance.add(1, 2) // => 3
{{< /code >}}

{{% aside info "Default import naming" %}}
Since there can be only one default export per module, the name by which you import the default export is not important - you can name it whatever you want.  For instance, instead of importing as `MyClass`, we could have said `import LuftBallons from 'myModule'`, and it would have worked just fine.  To read more about default and named exports, click [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export).
{{% /aside %}}

Named exports get a slightly more verbose syntax for importing, and the names _are_ important (otherwise it can't determine what you want to import).

{{< code js >}}
import { myNumber, sayHi } from 'myModule'

console.log(myNumber) // => 8

sayHi() // => 'hello'
{{< /code >}}

You can also combine default and named imports in the same line.

{{< code js >}}
import MyClass, { myNumber, sayHi } from 'myModule'
{{< /code >}}

## Projects

* [Dwarf Underground](https://github.com/xtbc17s1/dwarf-underground/)

## Homework

Add the "Add Thing" button, including the corresponding CSS.

### Bonus Credit

Make that button work!

### Super Mega Bonus Credit

Stop hard-coding _things_ altogether. Use only the things that were added via the "Add Thing" button.

### Super Mega Bonus Credit Hyper Fighting

Make the "remove" button work. 