+++
date = "2017-05-15T11:13:46-04:00"
title = "Day 5: Intro to React"
prev="/week2"
next="/week2/day6/"
toc = true
weight = 1

+++

<date>Monday, May 22, 2017</date>

## Lecture Videos

Morning:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [Day 5, part 1](https://www.youtube.com/watch?v=jiLLHIpYyQw&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=18) | [2](https://www.youtube.com/watch?v=dVfHMRBT4jE&index=23&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [3](https://www.youtube.com/watch?v=mYbMOp9mYZ0&index=19&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [4](https://www.youtube.com/watch?v=w6mIoGmGg34&index=20&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [5](https://www.youtube.com/watch?v=7ZkYasspRVU&index=21&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [6](https://www.youtube.com/watch?v=gwiGjyfGz1Y&index=22&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [7](https://www.youtube.com/watch?v=IJA_qlN7BFc&index=25&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [8](https://www.youtube.com/watch?v=xCSjpBUHqI4&index=26&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F)

Afternoon:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [Day 5, part 1](https://www.youtube.com/watch?v=sPn2ED9hZ1I&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=27) | [2](https://www.youtube.com/watch?v=a7eaK1Z5M5c&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=28) | [3](https://www.youtube.com/watch?v=9xKX0Tb6Yzk&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=29) | [4](https://www.youtube.com/watch?v=une1or5LnVM&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=30) | [5](https://www.youtube.com/watch?v=e4AaZu2vLKs&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=31) | [6](https://www.youtube.com/watch?v=F1bnQNnkOnE&index=32&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [7](https://www.youtube.com/watch?v=A0H3Th9WA7k&index=33&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [8](https://www.youtube.com/watch?v=slJzlsbhxDE&index=34&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG)

## Topics

### DOM Manipulation
* `contenteditable` - [MDN documentation](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/contenteditable)
* `keypress` events

### ES2015+ (ES6+)
* Inheritance (with the ES2015 `class` syntax; it's still _prototypal_ inheritance though) - [ES2015 classes on Babel](https://babeljs.io/learn-es2015/#ecmascript-2015-features-classes)
* Modules (import/export) - [ES2015 modules on Babel](https://babeljs.io/learn-es2015/#ecmascript-2015-features-modules)

### [React](https://facebook.github.io/react/)
* [Imperative vs. Declarative](https://tylermcginnis.com/imperative-vs-declarative-programming/)
* Components
  * JSX - [Docs: Introducing JSX](https://facebook.github.io/react/docs/introducing-jsx.html)
  * Props - [Docs: Components and Props](https://facebook.github.io/react/docs/components-and-props.html)
  * State - [Docs: State and Lifecycle](https://facebook.github.io/react/docs/state-and-lifecycle.html)
* [create-react-app](https://github.com/facebookincubator/create-react-app)

## Examples

### DOM Manipulation
`contentEditable` is a property that, like the name suggests, allows the content of an HTML element to be edited through user interaction with the DOM (similar to a text input field).

{{< code html >}}
&lt;div class=&quot;person-name&quot;&gt;Mark&lt;/div&gt;
&lt;button&gt;Click to Edit Name&lt;/button&gt;
{{< /code >}}

{{< code js >}}
const nameDiv = document.querySelector('.person-name')
console.log(nameDiv.isContentEditable) // => false

const button = document.querySelector('button')
button.addEventListener('click', (ev) => {
  nameDiv.contentEditable = true
  console.log(nameDiv.isContentEditable)
})

button.click() // => true (and div content will be editable)
{{< /code >}}

### React

#### Basic App
A basic React application requires a minimum of four things:

1. An HTML file with at least one empty element
2. The React library
3. One or more React Component(s)
4. A JavaScript call to attach the React Component to the empty element in step one

A minimal example:

{{< code html >}}
&lt;-- index.html --&gt;
&lt;html&gt;
  &lt;head&gt;
    &lt;title&gt;Basic React App&lt;/title&gt;
    &lt;script src=&quot;App.js&quot;&gt;&lt;/script&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;div id=&quot;app&quot;&gt;&lt;/div&gt;
  &lt;/body&gt;
&lt;/html&gt;
{{< /code >}}

{{< code jsx >}}
// App.js
class App extends React.Component {
  render() {
    return (
      &lt;h1&gt;Hello, world!&lt;/h1&gt;
    )
  }
}

ReactDOM.render(&lt;App /&gt;, document.querySelector('#app'))
{{< /code >}}

The body of the HTML above contains only an empty `div` with an id of 'app'.  This is where we will tell React to render our app. The `App.js` file defines the `App` component, and also makes the call to `ReactDOM.render`, which attaches `<App />` to the `div#app` element.

React will 'fill in' the div with the return result of the `App` component's `render` method, in this case, the markup `<h1>Hello, world!</h1>`.

#### Props

React components can be thought of as JavaScript functions.  They take in arguments, called `props`, and return markup that gets rendered to the page. Props can be just about anything, including strings, booleans, functions, objects, etc...

{{< code jsx >}}
class App extends React.Component {
  render() {
    return (
      &lt;h1&gt;Hello, {this.props.name}!&lt;/h1&gt;
    )
  }
}

&lt;App name=&quot;Bob&quot; /&gt;
{{< /code >}}

By passing in the string `"Bob"` to the `App` component, we can access that value from within the `App` class as a property on `this.props`.

Our rendered output would then be:

{{< code html >}}
&lt;h1&gt;Hello, Bob!&lt;/h1&gt;
{{< /code >}}

#### State

Components receive _props_ as arguments and cannot change their values. Data that needs to change belongs in _state_.

State should be initialized in the constructor and updated via `setState`.

{{% aside danger Do Not Modify State Directly %}}
Always use `setState` to modify a component's state. The only time you should set state directly is in the constructor.
{{% /aside %}}

{{< code jsx >}}
class App extends React.Component {
  constructor() {
    super()
    this.state = {
      count: 0
    }
  }

  increment(ev) {
    count = this.state.count + 1
    this.setState({ count })
  }

  render() {
    return (
      &lt;button type="button" onClick={this.increment.bind(this)}&gt;
        Click to Increment
      &lt;/button&gt;
      &lt;p&gt;
        Button has been clicked {this.state.count} times
      &lt;p&gt;
    )
  }
}

&lt;App /&gt;
{{< /code >}}

#### Modules

With [modules](https://babeljs.io/learn-es2015/#ecmascript-2015-features-modules), you can define each component in separate files, importing them as needed.

**Header.js**

{{< code jsx >}}
class Header extends React.Component {
  render() {
    return (
      &lt;h1&gt;Hello, {this.props.name}!&lt;/h1&gt;
    )
  }
}

export default Header
{{< /code >}}

**App.js**

{{< code jsx >}}
import Header from './Header'

class App extends React.Component {
  render() {
    return (
      &lt;Header name=&quot;Bob&quot; /&gt;
    )
  }
}

export default App
{{< /code >}}

## Presentations

* [Intro to React](/05-intro-to-react.pdf)

## Projects

* Megaroster (final): [morning](https://github.com/xtbc17s1/megaroster/tree/3ccd25f25db46ecff45a5b86ba32affcfb730f2d) | [afternoon](https://github.com/xtbc17s1/megaroster/commit/fc97404dada2d594970f64e9e4fbd3e9b3f6a271)
* Reactrobats on CodePen: [morning](https://codepen.io/dstrus/pen/BRvLNg/) | [afternoon](https://codepen.io/dstrus/pen/XRoMmR/)
* [Dwarf Underground](https://github.com/xtbc17s1/dwarf-underground/tree/3da6c4b4447d32404a141344867a457fdb9c3e60)

## Homework

* Split the page into at least 6 total components

### Bonus Credit

* Split the page into at least 10 total components, including components *in* components

### Super Bonus Credit

* Render the four article links at the bottom of the screen using `map` and passing in the props they need

### Super Mega Bonus Credit

* Make a component that contains a text field for leaving a comment
* Have the text field appear only when the 'comments' link at the bottom of the article is clicked

### Super Mega Bonus Credit Hyper Fighting

* Actually display comments that are entered and submitted