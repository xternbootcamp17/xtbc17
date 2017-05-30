+++
date = "2017-05-30T09:40:47-04:00"
title = "Routing and Fetching"
prev="/week3"
toc = true
weight = 1

+++

<date>Tuesday, May 30, 2017</date>

## Lecture Videos

Morning:

* [Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [1](https://www.youtube.com/watch?v=uijEhxd85mY&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=54)

## Topics

### Deployment

* GitHub Pages [↓](#deployment-github-pages)
* Firebase [↓](#deployment-firebase)

### Routing

* React Router v4
  * `<Router />`
  * Links and NavLinks
  * Routes
  * `history`

### Fetching Data

* The Fetch API
* Promises
* Parsing the response

## Examples

### Deployment: GitHub Pages

Deploying an app like Thing List is fairly simple, as it runs entirely on the client side (the browser). _create-react-app_ makes it even easier.

{{% aside info Note %}}
_create-react-app_ includes detailed instructions for [deploying with GitHub Pages](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md#github-pages) in the README.
{{% /aside %}}

Start by running the included _build_ script.

{{< term >}}
yarn build
{{< /term >}}

or

{{< term >}}
npm run build
{{< /term >}}

This builds the browser-ready version of our app in a `build` directory. (There are several aspects of our `src` directory that make it less than ideal for production use. For example, recall that our app is written using JSX, which browsers don't understand.)

It also prints out these instructions:

{{< term output="1,2,3,4,5" >}}
The project was built assuming it is hosted at the server root.
To override this, specify the homepage in your package.json.
For example, add this to build it for GitHub Pages:

  "homepage" : "http://myname.github.io/myapp",
{{< /term >}}

To host the app on GitHub Pages ([learn more about GitHub Pages](https://pages.github.com/)), add the line to `package.json`, just like it says, substituting your GitHub user name and repository name. In my case:

{{< code lang="json" class="line-numbers" line="3" >}}
  "name": "thing-list",
  "version": "0.1.0",
  "homepage": "http://xtbc17s1.github.io/thing-list",
{{< /code >}}

Now run `yarn build` again.

{{< term >}}
yarn build
{{< /term >}}

This time, the output will include some more specific instructions.

{{< term output="1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18" >}}
The build folder is ready to be deployed.
To publish it at http://xtbc17s1.github.io/thing-list, run:

  yarn add --dev gh-pages

Add the following script in your package.json.

    // ...
    "scripts": {
      // ...
      "predeploy": "npm run build",
      "deploy": "gh-pages -d build"
    }

Then run:

  yarn run deploy

{{< /term >}}

Cool! Let's add the `gh-pages` package.

{{< term >}}
yarn add --dev gh-pages
{{< /term >}}

or

{{< term >}}
npm install --save-dev gh-pages
{{< /term >}}

Now let's add those two scripts to `package.json`.

{{< code lang="json" class="line-numbers" line="6-7" >}}
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test --env=jsdom",
    "eject": "react-scripts eject",
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build"
  }
{{< /code >}}

Now whenever you're ready to deploy, you can just run `yarn deploy`!

{{< term >}}
yarn deploy
{{< /term >}}

or

{{< term >}}
npm run deploy
{{< /term >}}

And your app will be available at the homepage listed in your `package.json`&mdash;in my case, [http://xtbc17s1.github.io/thing-list](http://xtbc17s1.github.io/thing-list).

### Deployment: Firebase

Firebase offers free hosting in addition to the database and authentication solutions that we're already using. This again works quite well with _create-react-app_.

{{% aside info Note %}}
_create-react-app_ includes detailed instructions for [deploying with Firebase](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md#firebase) in the README.
{{% /aside %}}

First, install the command-line interface (CLI) for Firebase.

{{< term >}}
yarn global add firebase-tools
{{< /term >}}

or

{{< term >}}
npm install -g firebase-tools
{{< /term >}}

Now initialize Firebase in your project directory...

{{< term >}}
firebase init
{{< /term >}}

... and follow the [instructions from the _create-react-app_ README](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md#firebase).

{{% aside danger Warning %}}
If you've already configured your app to deploy to GitHub Pages, you need to remove the `homepage` line from `package.json` before deploying to Firebase.
{{% /aside %}}

### Routing

[React Router](https://github.com/ReactTraining/react-router) provides a routing solution that allows us to change what UI we render based on the current URL.  The router is a _Higher Order Component_ that wraps a React app and allows us to navigate without additional requests and responses to and from the server.

#### Router Setup

Setting up React Router is easy.  For web projects, install `react-router-dom`

{{< term >}}
yarn add react-router-dom  # install react router with yarn
{{< /term >}}

or

{{< term >}}
npm install --save react-router-dom  # install react router with npm
{{< /term >}}

Then, in your `ReactDOM.render` call, attach the Router as your base element, wrapping the root-level `<App />` component.  The whole app is now contained within the Router component, so we can take advantage of it anywhere.

**index.js**

{{< code jsx >}}
import React from 'react'
import ReactDOM from 'react-dom'
import { BrowserRouter as Router } from 'react-router-dom'
import App from './App'

ReactDOM.render(
  &lt;Router&gt;
    &lt;App /&gt;
  &lt;/Router&gt;,
  document.getElementById('root')
)
{{< /code >}}

#### Routes

The core of React Router is the `<Route />` component.  It allows you to specify what UI to render when a particular URL is matched.  For instance, if we wanted to render a `<Users />` component when we matched a `/users` URL, we could make the following Route:

{{< code jsx >}}
&lt;Route path='/users' component={Users} /&gt;
{{< /code >}}

If you don't want to render a whole component, a Route can alternatively accept a `render` prop, which accepts a function that returns JSX:

{{< code jsx >}}
&lt;Route path='/users' render={() => &lt;h1&gt;Users Path!&lt;/h1&gt;} /&gt;
{{< /code >}}

One important thing to keep in mind is that if we define a Route's path as `/users`, that will match both `/users` _and_ `/users/123`, because both begin with `/users`.  If we want the Route to match only when the path is _exactly_ `/users`, we can add the prop `exact` to our Route component.

{{< code jsx >}}
&lt;Route exact path='/users' component={Users} /&gt;
{{< /code >}}

#### Links

React Router also provides `<Link />` and `<NavLink />` components to make it easy to generate links to Routes. If we want to generate a Link that goes to `/about`, we can do the following:

{{< code jsx >}}
&lt;Link to='/about'&gt;About&lt;/Link&gt;
{{< /code >}}

NavLinks are similar, but provide some additional functionality.  The main difference is that they will add an `activeClassName` to the rendered link if the current URL matches the `to` property of the NavLink.  This allows active links to be styled differently than inactive links.

{{< code jsx >}}
&lt;NavLink to='/'&gt;Home&lt;/NavLink&gt;    // rendered link tag will have '.active' class when URL is '/'
{{< /code >}}

#### History

The `history` object is maintained and updated by the Router to keep track of where the user has navigated within the app.  It is passed to every component contained within the Router as part of the component's `props`.  It has a variety of helpful properties and methods that provide information and navigation. Here are just a few:

{{< code js >}}
history.length             // number of history entries
history.location           // provides the current location
history.push(path)         // navigates to a new path
history.go(n)              // navigates n steps through history stack
history.goBack()           // go back one step (history.go(-1))
history.goForward()        // go forward one step (history.go(1))
history.block(prompt)      // block navigation
{{< /code >}}

### Fetch

> The Fetch API provides a JavaScript interface for accessing and manipulating parts of the HTTP pipeline, such as requests and responses.  It also provides a global `fetch()` method that provides an easy, logical way to fetch resources asynchronously across the network.

[_MDN - Using Fetch_](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)

If we need to get data from a remote server (or send some to one), there are several ways to do it.  In vanilla JS, there is `XMLHttpRequest`, jQuery provides `$.ajax`, and there are a variety of other packages and libraries that provide their own version.  Luckily, there is a new kid in vanilla JS town - the _Fetch API_.

`fetch()` is a globally available, easy to use way to asynchronously send and receive data.  The simplest usage of fetch is to simply provide it with the URL of the request, and it will perform a `GET` request by default.  The `fetch()` function returns a promise that resolves when the data is received.  Once it is received, we can process and use the data with functions provided to the promise's `.then()` callbacks.

{{< code js >}}
fetch('https://api.mywebsite.com/users')    // fetch users data from 'mywebsite' api
  .then(response => response.json())        // parse the response json into JavaScript object(s)
  .then(users => console.log(users))        // log the parsed users to the console
  .catch(error => console.warn(error))      // if any errors occur, log them to the console
{{< /code >}}

{{% aside info "Fetch does more than just fetch" %}}
If no second argument is provided to `fetch()`, it defaults to a standard `GET` request.  However, the second argument can be a configuration object, allowing it to use different HTTP methods, set Headers, include Credentials, etc.  To find out more, check out [the docs](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
{{% /aside %}}

## Projects

API Party [morning]() | [afternoon] ()

## Homework

Extend the API-Party app by adding at least one additional route that gets data from a public API.

* A link to the route should appear in the header along with the 'Github' and 'NASA' links
* When the link is clicked, it should be styled to show that it is active
* The new component should fetch data from a public API
* Some interesting data from the API should be presented
* The data should look pretty (style it with CSS)

### Bonus Credit

* Accept user input to refine the data you request from the API

### Super Mega Bonus Credit

* Add additional routes and APIs

### Super Mega Bonus Credit Hyper Fighting

* Figure out something interesting to do with the data on your own.  Make a graph, render a map, add child routes, go nuts!

