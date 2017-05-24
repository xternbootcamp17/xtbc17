+++
date = "2017-05-15T11:13:46-04:00"
title = "Day 7: Firebase"
prev="/week2/day6/"
toc = true
weight = 3

+++

<date>Wednesday, May 24, 2017</date>

## Lecture Videos

Morning:

* [Full Playlist]() | [Day 6, part 1]() | [2]() | [3]() | [4]() | [5]() | [6]() | [7]()

Afternoon:

* [Full Playlist]() | [Day 6, part 1]() | [2]() | [3]() | [4]() | [5]() | [6]() | [7]()

## Topics

### React

* Methods as props
* Component lifecycle methods ([Docs](https://facebook.github.io/react/docs/react-component.html))
  * [`componentDidMount()`](https://facebook.github.io/react/docs/react-component.html#componentdidmount)
* `react-contenteditable` package ([on GitHub](https://github.com/lovasoa/react-contenteditable))

### JavaScript

* Property initializers + arrow functions

### Firebase

* Getting started
* Database rules
* Re-base for syncing React state with Firebase

## Examples

### React

#### Methods as props

Sometimes one component needs to update another component's state. It can't do that directly, but it can call a method from that other component if it's available via a prop.

[**Try this example live on CodePen**](https://codepen.io/dstrus/pen/bWzWew?editors=1010)

{{< code lang="jsx" line="5,23" class="line-numbers" >}}
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

### Firebase

#### Getting Started

[Firebase](https://firebase.google.com/) is a real-time database hosted by Google.  In addition to the database, it also provides features of authentication, analytics, cloud storage, and hosting.  For _Thing List_, we synced the `state` of our app to our database on Firebase.  This allowed all of our data to be persisted, even after page refreshes.

[Re-base](https://github.com/tylermcginnis/re-base) is an open source package that allows easy syncing of local state with a Firebase database. Add rebase to your project with one of the following commands:

{{< term >}}
yarn add re-base               # add package using yarn
npm install --save re-base     # add package using npm
{{< /term >}}

Once you have re-base installed, setup is easy!  First, create a new project on Firebase, then click on "Add to a web app" to see your JavaScript config object.  Next, initialize a Firebase app and database in your project using the config object, and provide the database to re-base.

{{< code js >}}
import Rebase from 're-base'
import firebase from 'firebase/app'
import database from 'firebase/database'

const app = firebase.initializeApp({
  apiKey: "YOURAPIKEY",
  authDomain: "YOURAUTHDOMAIN",
  databaseURL: "YOURDATABASEURL",
  projectId: "YOURPROJECTID",
  storageBucket: "YOURSTORAGEBUCKET",
  messagingSenderId: "YOURSENDERID"
})

const db = database(app)
const base = Rebase.createClass(db)

export default base
{{< /code >}}

Finally, call `base.syncState` to sync your app's local state with Firebase.  The first argument to `syncState` is the name of the Firebase endpoint you want to sync, and the second is a configuration object.

{{< code js >}}
base.syncState('myFavoriteEndpoint', {
  context: this,
  state: 'items'
})
{{< /code >}}

Now, any time we update the state of our app, the changes will sync with Firebase in real time.

{{% aside info "More Re-base Options" %}}
Re-base can do much more than just syncing state.  There are methods for `fetch`, `push`, `post`, etc.  To find out more about what all you can do with re-base, check out the [README](https://github.com/tylermcginnis/re-base#re-base)
{{% /aside %}}

#### Rules

For your Firebase database, you can set up rules (written in JSON) that specify the conditions under which data is allowed to be read or written.  By default, a newly generated project will require that a user be authenticated to read or write _any_ data.

{{< code js >}}
{
  "rules": {
    ".read": "auth != null",
    ".write": "auth != null"
  }
}
{{< /code >}}

If you do not have authentication set up yet, these values can be set to `true`.  This allows _anyone_ to read or write any data in the database.  This can be convenient, but probably not a good idea long-term (and you _will_ get a warning if you do that).

Additional rules can be applied per endpoint:

{{< code js >}}
{
  "rules": {
    "emails": {
      ".read": true,
      ".write": "auth != null"
    },
    "texts": {
      ".read": true,
      ".write": "auth != null"
    },
    "users": {
      "$userId": {
        ".read": "auth != null && auth.uid == $userId",
        ".write": "auth != null && auth.uid == $userId"
      }
    }
  }
}
{{< /code >}}

The above rules translate to:

* texts and emails can be read by anyone, but only written by authenticated users
* users data can be read and written only by an authenticated user whose `uid` matches the `$userId` of that item

## Projects

* ThingList [morning](https://github.com/xtbc17s1/thing-list/tree/23bd5cd351313500c971d4fbded85a0fbc656c0f) | [afternoon]()

## Homework

* When the checkbox is checked, mark the corresponding Thing as _completed_.
* Be sure this gets synced to Firebase and persists across page refreshes.

### Super Mega Bonus Credit

* Add a due date to each thing.
* Make sure it persists

**Hint**: HTML 5 includes an input type **date**, _i.e._ `<input type="date" />`