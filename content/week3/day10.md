+++
date = "2017-05-31T09:54:15-04:00"
title = "Review and NoteHerder"
prev = "/week3/day9"
next = "/week3/day10"
toc = true
weight = 2

+++

<date>Wednesday, May 31, 2017</date>

## Lecture Videos

Morning:

* [Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [1](https://www.youtube.com/watch?v=LbXfZTiTeIk&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=55) | [2](https://www.youtube.com/watch?v=FJkPBapdxa4&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=56) | [3](https://www.youtube.com/watch?v=MBdNv10wMiw&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=57) | [4](https://www.youtube.com/watch?v=hI1qt26ZAc0&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=58) | [5](https://www.youtube.com/watch?v=N-XYDqyKvf0&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=59) | [6](https://www.youtube.com/watch?v=V9XID50VYi8&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=60)

Afternoon:

* [Playlist](https://www.youtube.com/watch?v=1ZYirXVMKmc&index=77&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [1](https://www.youtube.com/watch?v=vjg4jiZVtGQ&index=83&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [2](https://www.youtube.com/watch?v=w6xXc6bsFeQ&index=84&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [3](https://www.youtube.com/watch?v=x_cHt4zKgWY&index=85&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [4](https://www.youtube.com/watch?v=BozRAQuVyAI&index=86&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [5](https://www.youtube.com/watch?v=uTifw6rEYMI&index=87&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG)

## Topics

### Homework Showcase

#### Morning

* [Laurence's Project](https://github.com/yodasodabob/api-party) - New NASA route that gets pictures from the [_EPIC API_](https://api.nasa.gov/api.html#EPIC)
* [Ian's Project](https://github.com/izanger/api-party) - Gets historical events from [_This Day In History API_](http://history.muffinlabs.com/#api)
* [Mohak's Project](https://github.com/MohakC/api-party) - Pokemon data from [_The PokeAPI_](https://pokeapi.co/)
* [Steve's Project](https://github.com/sbenchik/api-party) - Today's weather forecast by location from [_OpenWeatherMap API_](https://openweathermap.org/api)

#### Afternoon

* [Charley's Project](https://github.com/charleydrewwolak/api-party) - Pokemon data from [_The PokeAPI_](https://pokeapi.co/)
* [Trent's Project](https://github.com/trentspi/api-party) - Find and display videos from [_YouTube API_](https://developers.google.com/youtube/iframe_api_reference)
* [Nicholas's Project](https://github.com/nfordyc/api-party) - Run mathematical calculations using the [_Newton API_](https://github.com/aunyks/newton-api)
* [Eric's Project](https://github.com/EricChavarria/api-party) - Pokemon data from [_The PokeAPI_](https://pokeapi.co/) (with tables of stats!)
* [Clayton's Project](https://github.com/winderscm/api-party) - Compare crypto-currency values with data from the [_CryptoCompare API_](https://www.cryptocompare.com/api/)

### Noteherder

[Noteherder](https://github.com/xtbc17s1/noteherder) is a note-taking app built with a React front-end.  It utilizes Firebase as back-end for authentication and data storage.  Much of the basic functionality is similar to _ThingList_ - it renders a list of notes (aka things), with the ability to create, read, update, and delete notes.  Also, like _ThingList_, it uses Github OAuth authentication for user sign-in and allowing for scoping of notes to users.

However, there are many new concepts as well. We'll go over some of those here.

#### Private and Public Routes

We are already familiar with the `<Route />` component provided by React Router, but what if we want to create specialized routes that only allow access based on the presence of an authorized user?  We can use the concept of [_composition_](https://facebook.github.io/react/docs/composition-vs-inheritance.html) to create specialized versions of `<Route />` that we'll call `<PrivateRoute />` and `<PublicRoute />`.

**RouteHelpers.js**

{{< code jsx >}}
export function PrivateRoute({component: Component, render, authed, ...rest}) {
  return (
    &lt;Route
      {...rest}
      render={(props) => authed
        ? (render && render()) || &lt;Component {...props} /&gt;
        : &lt;Redirect to={{pathname: '/sign-in', state: {from: props.location}}} /&gt;}
    />
  )
}

export function PublicRoute({component: Component, render, authed, ...rest}) {
  return (
    &lt;Route
      {...rest}
      render={(props) => !authed
        ? (render && render()) || &lt;Component {...props} /&gt;
        : &lt;Redirect to='/notes' /&gt;}
    />
  )
}
{{< /code >}} 

Let's talk through the code for `PrivateRoute`.  As you can see, it is essentially a stateless functional component that is a wrapper around a `Route` component.  In the `Route`'s render method is a ternary statement that checks whether there is a valid user passed to it (the `authed` prop).

If there is an `authed` user, the `Route` does one of two things - run the `render` method passed in as a prop (if there is one), or render a `Component` passed in as a prop.

If there is not an `authed` user, the `Route` renders a `<Redirect />` component (part of React Router) that redirects the user to the `'/sign-in'` path.

`PublicRoute` is very similar, except it checks to make sure that there is _not_ an `authed` user.  If there is not a user, it runs the `render` method or renders a `Component`.  If there _is_ an `authed` user, it redirects to `'/notes'`.

#### Rich Text Editor

In _ThingList_, we used `contenteditable` to allow us to input new text into a _Thing_, but the user has no control over how the text looks.  For a more fully-featured app, wouldn't it be nice to have the ability to do bold text, italics, change font size, etc...?  Well good news, you can totally do that thing.  There are a variety of _WYSIWYG_ editors that can be added to your application to give the user far more formatting options for their text input.  The editor used in Noteherder is called, appropriately, [React Rich Text Editor](https://github.com/sstur/react-rte).

{{< term >}}
yarn add react-rte                # install using yarn

npm install --save react-rte      # install using npm
{{< /term >}}

Once the package is added to your project, we can import and use the `<RichTextEditor />` component anywhere we need a rich text editor.

**NoteForm.js (simplified)**

{{< code jsx >}}
import RichTextEditor from 'react-rte'

class NoteForm extends Component {
  state = {
    editorValue: RichTextEditor.createEmptyValue()
    note: {
      title: '',
      body: ''
    }
  }

  handleEditorChange = (editorValue) => {
    const note = {...this.state.note}
    note.body = editorValue.toString('html')
    this.setState({ note, editorValue })
  }

  render() {
    return (
      &lt;form&gt;
        &lt;RichTextEditor
          name="body"
          value={this.state.editorValue}
          onChange={this.handleEditorChange}
        /&gt;
      &lt;/form&gt;
    )
  }
}
{{< /code >}}

## Projects

[Noteherder](https://github.com/xtbc17s1/noteherder) - source code

## Homework

Read through the code for Noteherder and make sure you understand how the app works.  Reading other people's code is an extremely valuable skill to have.

Finish your API-party homework if it is not yet complete and functional.
