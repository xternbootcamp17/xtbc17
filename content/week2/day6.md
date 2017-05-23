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

## Presentations

## Projects

* [Dwarf Underground](https://github.com/xtbc17s1/dwarf-underground/)

## Homework

### Bonus Credit

### Super Bonus Credit

### Super Mega Bonus Credit

### Super Mega Bonus Credit Hyper Fighting
