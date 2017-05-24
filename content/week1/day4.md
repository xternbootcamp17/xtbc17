+++
date = "2017-05-18T11:29:27-04:00"
title = "Day 4: LocalStorage and JavaScript Classes"
toc = true
weight = 4
prev="/week1/day3"
next="/week1/day4"

+++

<date>Thursday, May 18, 2017</date>

## Lecture Videos

Morning:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [Day 4, part 1](https://www.youtube.com/watch?v=YGj8J6MceYg&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=11) | [2](https://www.youtube.com/watch?v=zvYmxL1ojaI&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=12) | [3](https://www.youtube.com/watch?v=MALqYKxz9-Y&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=13) | [4](https://www.youtube.com/watch?v=8wfKQnitrmY&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=14) | [5](https://www.youtube.com/watch?v=2l7bv4a3S-s&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=15) | [6](https://www.youtube.com/watch?v=59thZz_yFgE&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=16) | [7](https://www.youtube.com/watch?v=w-bqy6n8Gco&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=17)

Afternoon:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [Day 4, part 1](https://www.youtube.com/watch?v=mpEFSr8eXEY&index=16&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [2](https://www.youtube.com/watch?v=IkNAVmWuPDU&index=17&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [3](https://www.youtube.com/watch?v=i2XL0mV1qmU&index=18&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [4](https://www.youtube.com/watch?v=3KIvEuhPJag&index=19&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [5](https://www.youtube.com/watch?v=gTiMSnn-4nU&index=20&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [6](https://www.youtube.com/watch?v=xd2ewpDX_yE&index=21&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [7](https://www.youtube.com/watch?v=NixaLyI35HU&index=22&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [8](https://www.youtube.com/watch?v=0U5F5qO9cv4&index=23&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [9](https://www.youtube.com/watch?v=YrEgnscYuO4&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=24) | [10](https://www.youtube.com/watch?v=KS47lxLSYvc&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=25) | [11](https://www.youtube.com/watch?v=VSDpPnlZ3ig&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=26)

## Topics

### `localStorage` [↓](#localstorage)
* [Using `localStorage`]((https://www.smashingmagazine.com/2010/10/local-storage-and-how-to-use-it/))
* `JSON.stringify`
  * [Using `JSON.stringify`](http://www.dyn-web.com/tutorials/php-js/json/stringify.php)
  * [Live example](http://jsfiddle.net/queryj/hLkUz/)
  * [API reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify), including optional arguments for whitelisting properties and transforming the data as it's stringified
* `JSON.parse`
  * [Using `JSON.parse`](http://www.dyn-web.com/tutorials/php-js/json/parse.php)
  * [API reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse), including optional argument for transforming the data as it's parsed

### Font Awesome [↓](#font-awesome)
* [Docs](http://fontawesome.io/)
* [Examples](http://fontawesome.io/examples/)
* [Icon list](http://fontawesome.io/icons/)
* [Font Awesome intro](http://www.w3schools.com/icons/fontawesome_icons_intro.asp) on w3schools, including a live editor
* [Icon Fonts &amp; Accessibility](http://fontawesome.io/accessibility/)

### Foundation
* [Button](http://foundation.zurb.com/sites/docs/button.html)
* [Button Group](http://foundation.zurb.com/sites/docs/button-group.html)
* [Forms](http://foundation.zurb.com/sites/docs/forms.html)

### CSS Selectors
**[Child and sibling selectors](https://css-tricks.com/child-and-sibling-selectors/)**

* [Descendant selector (_space_)](https://css-tricks.com/almanac/selectors/d/descendant/)
* [`>` combinator - child selector](https://css-tricks.com/almanac/selectors/c/child/)
* [`+` combinator - adjacent sibling selector)](https://css-tricks.com/almanac/selectors/a/adjacent-sibling/)
* [`:first-child` pseudo-class selector](https://css-tricks.com/almanac/selectors/f/first-child/)
* [`:last-child` pseudo-class selector](https://css-tricks.com/almanac/selectors/l/last-child/)

### Array methods
* [`Array.prototype` documentation on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/prototype?v=control)
* [`reverse()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse?v=control)
* `find()` - [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find?v=control) | [w3schools](https://www.w3schools.com/jsref/jsref_find.asp)
* `findIndex()` - [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex?v=control) | [w3schools](https://www.w3schools.com/jsref/jsref_findindex.asp)

### JavaScript Classes [↓](#javascript-classes)
* Class declarations
* The `constructor` function
* Methods
* Instantiating objects from a class

### Chrome Developer Tools
* [Accessing recently inspected elements with `$0`-`$4`](https://willd.me/posts/0-in-chrome-dev-tools) ([official docs](https://developers.google.com/web/tools/chrome-devtools/console/command-line-reference#0_-_4))
* [Inspecting storage from the _Application_ panel](https://developers.google.com/web/tools/chrome-devtools/manage-data/local-storage)

## Examples
### localStorage

`localStorage` is storage in your web browser that conforms to Web Storage API.  It is scoped by domain, meaning other websites cannot access data stored by your website and vice versa.  The data in `localStorage` persists in the browser until removed, even if the browser is closed and re-opened.

To set an item, use `localStorage.setItem`, and retrieve data using `localStorage.getItem`.  It is important to remember that values stored will always be strings, so it may be use necessary to use the `JSON.stringify` and `JSON.parse` methods to set and retrieve non-string data.  JSON stands for **J**ava**S**cript **O**bject **N**otation.  To learn more about JSON, click [here](https://www.w3schools.com/js/js_json_intro.asp).

{{< code js >}}
const myObject = {
  thisIsCool: true
}

localStorage.setItem('myObject', myObject)
localStorage.getItem('myObject') // => "[object Object]"
// localStorage saves the result of the implicit myObject.toString() call

localStorage.setItem('myObject', JSON.stringify(myObject))
// calling JSON.stringify converts the object to a JSON string representation
// so it can be stored in localStorage without loss of data

const retrievedObject = localStorage.getItem('myObject') // => "{"thisIsCool":true}"
JSON.parse(retrievedObject) // => {thisIsCool: true}
// JSON.parse converts the retrieved JSON string back into a JavaScript object
{{< /code >}}

### Font Awesome

Font Awesome provides hundreds of vectorized, professional-looking icons for free.  Once you have the Font Awesome stylesheet downloaded and included in your project, use `<i>` tags with appropriate classes to render the icons you want.

{{< code html >}}
&lt;-- Sample link tag to include Font Awesome in HTML --&gt;
&lt;link rel=&quot;stylesheet&quot; href=&quot;css/font-awesome.min.css&quot;&gt;&lt;i&gt;

&lt;-- Renders a sweet camera icon --&gt;
&lt;i class=&quot;fa fa-camera-retro&quot;&gt;&lt;/i&gt;
{{< /code >}}

### CSS Selectors

{{< code html >}}
&lt;div&gt;
  &lt;p&gt;paragraph one&lt;/p&gt;
  &lt;p&gt;paragraph two&lt;/p&gt;
  &lt;p&gt;paragraph three&lt;/p&gt;
&lt;/div&gt;
&lt;p&gt;paragraph four&lt;/p&gt;
{{< /code >}}

{{< code css >}}
p:first-child {
  /* selects any paragraph that is the first child of its parent (paragraph one) */
}

p:last-child {
  /* selects any paragraph that is the last child of its parent (paragraph three) */
}

div > p {
  /* selects any paragraph that is a child of a div (paragraphs one, two, and three) */
}
{{< /code >}}

### JavaScript Classes

JavaScript is not a class-based language like C++, Java, or Ruby.  It uses [prototypal inheritance](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain) instead.  However, as of ES2015, the `class` keyword was added to the language to provide a more concise syntax and similarity to popular class-based languages.

A class is essentially a constructor of Objects.  Methods and properties in the class will be inherited by each object that is constructed by the class.  Object instances are created by using the `new` keyword.  Classes have a `constructor` method, which is called when instances are created and allows for configuration of the object.

{{< code js >}}
class Dog {
  constructor() {
    this.furColor = 'brown'
  }

  bark() {
    console.log('WOOF')
  }
}

const bowser = new Dog();
bowser.furColor // => 'brown'
bowser.bark()   // => 'WOOF'
{{< /code >}}

Classes can also inherit from another class.  Inheritance is specified using the `extends` keyword.  When a class inherits from another, it has access to the methods and properties of *both* classes, although if both classes implement the *same* property or method, the child class will take precedence.

{{< code js >}}
class Animal {
  constructor() {
    this.furColor = 'brown'
  }

  speak() {
    console.log('Some sort of noise')
  }
}

class Dog extends Animal {
  constructor() {
    this.furColor = 'black'
  }

  bark() {
    console.log('WOOF')
  }
}

const bowser = new Dog()
bowser.furColor // => 'black'
bowser.speak()  // => 'Some sort of noise'
bowser.bark()   // => 'WOOF'

const rodent = new Animal()
rodent.furColor // => 'brown'
rodent.speak()  // => 'Some sort of noise'
rodent.bark()   // => Uncaught TypeError: rodent.bark is not a function
{{< /code >}}


## Presentations

* [Intro to localStorage](/04-local-storage.pdf)

## Projects

### Megaroster

[Morning](https://github.com/xtbc17s1/megaroster/tree/b3f42521a8c764fc7c956cb8a01ee322dc2b9e2b) | [Afternoon](https://github.com/xtbc17s1/megaroster/tree/443b3c889e4b7592bc842570c3a6c681b2900977)

## Homework

* Make "move down" work if you haven't already.
* Allow the editing of student names after they're already in the list. (Gee, it would be nice if I could make that span's _content editable_!)

### Super Mega Bonus Credit Hyper Fighting

Have a nice weekend!