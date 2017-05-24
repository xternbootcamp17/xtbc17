+++
date = "2017-05-15T11:13:46-04:00"
title = "Day 7: React"
prev="/week2/day6/"
toc = true
weight = 3

+++


<date>Wednesday, May 24, 2017</date>

## Topics

### React

* Methods as props
* Component lifecycle methods ([Docs](https://facebook.github.io/react/docs/react-component.html))
  * [`componentDidMount()`](https://facebook.github.io/react/docs/react-component.html#componentdidmount)
* `react-contenteditable` package ([on GitHub](https://github.com/lovasoa/react-contenteditable))

### JavaScript
* Property initializers + arrow functions

## Examples

### React

#### Methods as props

Sometimes one component needs to update another component's state. It can't do that directly, but it can call a method from that other component if it's available via a prop.

[**Try this example live on CodePen**](https://codepen.io/dstrus/pen/bWzWew?editors=1010)

{{< code lang="jsx" line="2,20" class="line-numbers" >}}
import React from 'react'
import ReactDOM from 'react-dom'

const PartyButton = ({ celebrate, celebrations }) =&gt; {
  return &lt;button onClick={celebrate}&gt;Party! {celebrations}&lt;/button&gt;
}

class App extends React.Component {
  constructor() {
    super()
    this.state = {
      celebrations: 0,
    }
    this.celebrate = this.celebrate.bind(this)
  }

  celebrate() {
    const celebrations = this.state.celebrations + 1
    this.setState({ celebrations })
  }

  render() {
    return &lt;PartyButton celebrate={this.celebrate} celebrations={this.state.celebrations} /&gt;
  }
}

ReactDOM.render(&lt;App /&gt;, document.querySelector('main'))
{{< /code >}}

#### Component lifecycle methods

**`componentDidMount()`** is invoked immediately after a component is mounted. Initialization that requires DOM nodes should go here.

{{< code jsx >}}
import React, { Component } from 'react'

class MyComponent extends Component {
  componentDidMount() {
    this.nameInput.focus()
  }

  render() {
    return (
      &lt;input 
        ref={(input) =&gt; { this.nameInput = input; }} 
        defaultValue="will focus"
      /&gt;
    )
  }
}
{{< /code >}}

#### `react-contenteditable` package

This package provides a React component for a div with editable contents, handling all the messy stuff (like `dangerouslySetInnerHTML`).

{{< code jsx >}}
import React from 'react'
import ContentEditable from 'react-contenteditable'

class MyComponent extends React.Component {
  constructor() {
    this.state = {
      html: &quot;&lt;strong&gt;Hello, &lt;em&gt;World&lt;/em&gt;!&lt;/strong&gt;&quot;
    }
    this.handleChange = this.handleChange.bind(this)
  }

  handleChange(ev) {
    this.setState({ html: evt.target.value })
  }

  render() {
    return (
      &lt;ContentEditable
        html={this.state.html}       // innerHTML of the editable div
        disabled={false}             // use true to disable
        onChange={this.handleChange} // handle innerHTML change
      /&gt;
    )
  }
}
{{< /code >}}

### JavaScript (ES6+)

#### Property initializers

Yesterday, we used property initializers to set a component's initial state without adding a constructor. Combining property initializers and arrow functions also gives us a convenient way to auto-bind `this`:

{{< code jsx >}}
class Something extends React.Component {
  handleButtonClick = (ev) => {
    // `this` is bound correctly!
    this.setState({ buttonWasClicked: true });
  }
}
{{< /code >}}