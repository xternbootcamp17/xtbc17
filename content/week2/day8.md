+++
date = "2017-05-25T09:34:51-04:00"
title = "Day 8: Authentication"
toc = true
prev="/week2/day7"
next="/week3/"
weight = 4

+++

<date>Thursday, May 25, 2017</date>

## Lecture Videos

Morning:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [Day 8, part 1](https://www.youtube.com/watch?v=KcKRs6EF2aQ&index=46&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [2](https://www.youtube.com/watch?v=PqBGnicbwBo&index=47&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [3](https://www.youtube.com/watch?v=Qgb9slE1Vy8&index=48&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [4](https://www.youtube.com/watch?v=Y4flcs43y2I&index=49&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [5](https://www.youtube.com/watch?v=Rs5qHdIcJdg&index=50&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [6](https://www.youtube.com/watch?v=Nqln3z3Qm3A&index=51&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [7](https://www.youtube.com/watch?v=w4Hm_YkP7O8&index=52&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [8](https://www.youtube.com/watch?v=NNhIOZ7scH8&index=53&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F)

Afternoon:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [Day 8, part 1](https://www.youtube.com/watch?v=MPwdC4keEa8&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=62) | [2](https://www.youtube.com/watch?v=fV4Nj-qyrCs&t=2s&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=63) | [3](https://www.youtube.com/watch?v=pyV2ch1Z6kc&t=1s&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=64) | [4](https://www.youtube.com/watch?v=hrUmU-Xe-5k&t=4s&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=65) | [5](https://www.youtube.com/watch?v=J60k6tSosfs&t=6s&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=66) | [6](https://www.youtube.com/watch?v=KQQqja3IlYg&t=3s&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=67) | [7](https://www.youtube.com/watch?v=zJgYth64v7U&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=68) | [8](https://www.youtube.com/watch?v=qDYMyPwjmCk&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=69) | [9](https://www.youtube.com/watch?v=CqLtfW4fdbc&t=655s&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=70) | [10](https://www.youtube.com/watch?v=9wrGqsY15ds&t=5s&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=71) | [11](https://www.youtube.com/watch?v=dfztTfau9qo&t=394s&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=72) | [12](https://www.youtube.com/watch?v=HkWNB-GCUPI&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=73) | [13](https://www.youtube.com/watch?v=yak0SVTJ9Zc&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=74)

## Topics

### Firebase Authentication

* 'firebase/auth'
* `authWithPopup`
* signing in and out
* handling auth state changes

## Examples

### Firebase Authentication

Firebase isn't just a real-time database.  It can also provide authentication services via email/password, phone, or common third-party services like Github, Facebook, and Google. For ThingList, we set up authentication via Github OAuth.

#### Step 1: Get your authorization callback URL from Firebase

Navigate to your project in Firebase console.  Click on the 'Authenticate' tab on the left and then on the Github logo.  Copy the authorization callback URL.

<div class="img firebase-enable-github"><span>The data for the Client ID and Client Secret will be generated in the next step.</span></div>

#### Step 2: Register your app in Github

Log in to Github and click on 'Settings'.  On the left hand side, click on 'OAuth Applications' under the 'Developer settings' menu.  Register a new app and fill out the form.

<div class="img github-oauth-new-registration"><span>Use the Authorization callback URL from step 1</span></div>

After successfully registering the app, you'll be taken to your new app's settings page.

<div class="img github-oauth-secrets"><span>Seeeeecrets...  (Don't worry, this app has been deleted. Never post your app secrets publicly.)</span></div>

#### Step 3: Enable Github authentication in Firebase

Go back to the Github authentication tab in Firebase and fill in the Client ID and Client Secret that you got from registering your app with Github.

<div class="img firebase-github-secrets"><span>More Seeeeecrets...  (But seriously, don't share your secrets)</span></div>

#### Step 4: Add Firebase auth to your app

_Note: This step assumes you already have your Firebase database added to your app._ 

Import `firebase/auth` into your app's firebase setup.  Enable firebase auth and also create an instance of `GithubAuthProvider`.

**base.js**

{{< code lang="js" line="4,17,18" class="line-numbers" >}}
import Rebase from 're-base'
import firebase from 'firebase/app'
import database from 'firebase/database'
import 'firebase/auth'

const app = firebase.initializeApp({
  apiKey: "",
  authDomain: "",
  databaseURL: "",
  projectId: "",
  storageBucket: "",
  messagingSenderId: ""
})

const db = database(app)

export const auth = app.auth()
export const githubProvider = new firebase.auth.GithubAuthProvider()

export default Rebase.createClass(db)
{{< /code >}}

#### Step 5: Set up the SignIn Component

Import `auth` and the `githubProvider` into whatever component handles the sign-in process.  Call `signInWithPopup` on the `auth` object, passing the provider as a parameter.  Then call an `authHandler` function when the promise resolves to handle whatever you want to do after authorization is successful.

**SignIn.js**

{{< code jsx >}}
import React from 'react'
import { auth, githubProvider } from './base'

const SignIn = ({ authHandler }) => {
  const authenticate = (provider) => {
    auth
      .signInWithPopup(provider)
      .then(authHandler)
  }

  return (
    &lt;button className="SignIn" onClick={() => authenticate(githubProvider)}&gt;
      Sign In With GitHub
    &lt;/button&gt;
  )
}

export default SignIn
{{< /code >}}

#### Step 6: Finishing sign-in

What the `authHandler` callback does is up to you, but for _ThingList_, we had it do pretty typical things - save the user ID to state, and initialize syncing our local state for 'things' with the data stored on Firebase.

**App.js**

{{< code js >}}
// ...

authHandler = (authData) => {
  this.setState(
    { uid: authData.user.uid },
    this.syncThings
  )
}

// ...
{{< /code >}}

#### Step 7: Handling auth state changes (and page refreshes)

What happens if auth state changes?  Or the user refreshes the page?  We should probably set up something to listen for that.  In the `componentWillMount` lifecycle hook that runs when the Component is first getting loaded, we can call the `onAuthStateChanged` method to set up such a listener.

**App.js**

{{< code js >}}
// ...

componentWillMount() {
  auth.onAuthStateChanged(
    (user) => {
      if (user) {
        this.authHandler({ user })
      }
    }
  )
}

// ...
{{< /code >}}

#### Step 8: Signing out

Signing out when using Firebase for authentication is quite simple - just call `auth.signOut()`!  Once the promise returned by `signOut` has resolved, you can handle any additional cleanup.  In _ThingList_, we just set `state.uid` back to `null`.

**App.js**

{{< code js >}}
// ...

signOut = () => {
  auth
    .signOut()
    .then(() => this.setState({ uid: null }))
}

// ...
{{< /code >}}

## Projects

* ThingList [morning](https://github.com/xtbc17s1/thing-list/tree/bb66ddd5b3a562f2dd3a20c1b284fe23b9f71b59) | [afternoon](https://github.com/xtbc17s1/thing-list/tree/040e15b7cbcb0d4c06c36940c2c12759b495fc73)

## Homework

**PRACTICE!**  Extend a project from class.  Write a new project.  Add a different type of authentication.  You know enough to start building things on your own, and it's definitely the best way to learn once you have the basics down.