+++
date = "2017-05-15T11:13:46-04:00"
title = "Day 6: React"
prev="/week2/day5/"
next="/week2/day7"
toc = true
weight = 2

+++

<date>Tuesday, May 23, 2017</date>

## Lecture Videos

Morning:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [Day 6, part 1](https://www.youtube.com/watch?v=oWb1IdhOl7A&index=26&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [2](https://www.youtube.com/watch?v=SsBUeaku12g&index=27&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [3](https://www.youtube.com/watch?v=IlUoLPsrHrE&index=28&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [4](https://www.youtube.com/watch?v=E01j6AcMSF4&index=29&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [5](https://www.youtube.com/watch?v=xytTTrggEyc&index=30&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [6](https://www.youtube.com/watch?v=9Dn6aMJMEHc&index=31&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [7](https://www.youtube.com/watch?v=Smzb6gGyz3w&index=32&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F)

Afternoon:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [Day 6, part 1](https://www.youtube.com/watch?v=1VOesxJNbIA&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=35) | [2](https://www.youtube.com/watch?v=yIiWHmuks1E&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=36) | [3](https://www.youtube.com/watch?v=rxXsCqzzi7A&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=37) | [4](https://www.youtube.com/watch?v=cGkv37JcAcM&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=38) | [5](https://www.youtube.com/watch?v=iz8oJX49tLA&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=39) | [6](https://www.youtube.com/watch?v=a1eQtVlx1Js&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=40) | [7](https://www.youtube.com/watch?v=xEBCLL8YYE0&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=41) | [8](https://www.youtube.com/watch?v=UjDVy0Qis4A&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=42) | [9](https://www.youtube.com/watch?v=ZuI0o8A-2nM&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=43) | [10](https://www.youtube.com/watch?v=e7UhOY48S7Q&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=44)

## Topics

### [React](https://facebook.github.io/react/)

* Using `map` with components
* Stateless Functional Components
* Conditional rendering

### JavaScript

* Named and default exports
* Named and default imports
* Property initializers
* Spread operator
* Destructuring assignment

### Package Managers

* [NPM](https://www.npmjs.com/) - Node Package Manager
* [Yarn](https://code.facebook.com/posts/1840075619545360) - Facebook's version of npm

### [CSS Specifity](https://specificity.keegan.st/)

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
      { name: 'Nichole', hair: 'long' },
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

If you need to import a named export under a different name&mdash;if, for example, you have another import or local variable with the same name&mdash;you can specifiy a different name using _as_.

{{< code js >}}
import { myNumber as num, sayHi as yo } from 'myModule'

console.log(num) // => 8

yo() // => 'hello'
{{< /code >}}

You can also combine default and named imports in the same line.

{{< code js >}}
import MyClass, { myNumber, sayHi } from 'myModule'
{{< /code >}}

#### Property initializers

From the proposal:

> "Class instance fields" describe properties intended to exist on instances of a class (and may optionally include initializer expressions for said properties).

We can take advantage of this in React.

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

{{% aside danger "Subject to  minor changes" %}}
[Property initializers](https://github.com/tc39/proposal-class-public-fields) are a [Stage 2 proposal](https://tc39.github.io/process-document/) for ECMAScript, meaning that it's still a _draft_ and is subject to minor changes before becoming standardized. Facebook itself is already using these techniques in production, however.
{{% /aside %}}

#### Spread operator

The [*spread operator*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator) was added in ES6 to allow an expression to be expanded in places where multiple arguments (for function calls) or multiple elements (for array literals) or multiple variables (for destructuring assignment) are expected.

{{< code js >}}
function myFunc (x, y, z) {
  console.log(x)
  console.log(y)
  console.log(z)
}
const args = [1, 2, 3]

myFunc(...args) // the spread '...args' applies the items in args to the three arguments in myFunc
// => 1
// => 2
// => 3
{{< /code >}}

It is also an easy way to make copies of iterable objects

{{< code js >}}
const ary = [1, 2, 3]
const aryCopy = [...ary] // makes a copy of ary
{{< /code >}}

If you are in a project using Babel (like a React project created with `create-react-app`), you can also use the `object-rest-spread-transform` to apply this same method to objects.

{{< code js >}}
this.state = {'a': true, party: 'hard'}
const stateCopy = {...this.state} // makes a copy of this.state
{{< /code >}}

#### Destructuring assignment

[Destructuring assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) syntax is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.

{{< code js >}}
const myObj = {
  a: true,
  b: 'Destructuring!'
}

let { a, b } = myObj

console.log(a) // => true
console.log(b) // => 'Destructuring!'
{{< /code >}}

### Package Managers

#### Node Package Manager (npm)

Node Package Manager hosts almost half a million packages of free, reusable JavaScript code and is the largest software registry in the world. It allows you to easily add any module to your project, and it will install the requested package, as well as any required dependencies of that package.

{{< term >}}
npm install react
{{< /term >}}

#### Yarn

[Yarn](https://code.facebook.com/posts/1840075619545360) is Facebook's version of npm, designed to improve performance and resolve several important issues.  The key differences are:

* Deterministic installation - packages will always install in the same order on every machine
* `yarn.lock` - this lockfile locks dependency versions for consistency and security
* Local cache of downloaded packages - faster and can still work with no internet connection after initial installation
* Parallel installation - Dependency installation can happen in parallel, greatly increasing speed

To install yarn (npm was already installed as part of setup instructions), type the following command:

{{< term >}}
npm install -g yarn
{{< /term >}}

Once installed, you can use yarn with following commands:

{{< term >}}
yarn
# installs all packages and dependencies listed in your project's package.json

yarn add {package_name}
# installs a new package and adds it to package.json

yarn start
# starts your local development web server (in project from create-react-app)
{{< /term >}}

## Projects

* Dwarf Underground: [morning](https://github.com/sbaughman/dwarf-underground/tree/2330778425ae10658dadcd974b93aefd361c0bef) | [afternoon](https://github.com/xtbc17s1/dwarf-underground/tree/599b3a3ac93da57e55aa898333b97d23c8169efb)
* Static HTML/CSS for Thing List: [thing-list-static](https://github.com/xtbc17s1/thing-list-static)
* ThingList: [morning](https://github.com/xtbc17s1/thing-list/tree/3f7652d667e3c46342e6f7e90b9ca54d0951d6a3) | afternoon

## Homework

Add the _Add Thing_ button, including the corresponding CSS.

### Bonus Credit

Make that button work!

### Super Mega Bonus Credit

Stop hard-coding _things_ altogether. Use only the things that were added via the _Add Thing_ button.

### Super Mega Bonus Credit Hyper Fighting

Make the _remove_ button work. 