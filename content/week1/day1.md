+++
date = "2017-05-15T11:13:46-04:00"
title = "Day 1: Introduction"
next="/week1/day2"
prev="/week1"
toc = true
weight = 1

+++

<date>Monday, May 15, 2017</date>

## Topics
* History of JavaScript and the Web
* Getting the most out of a coding bootcamp
* Anatomy of an HTML element ([tags](https://developer.mozilla.org/en-US/docs/Web/HTML/Element), [attributes](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes), [text content](https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent))
* Basic CSS selector syntax
  * Element name (`div`, `h1`, `p`, etc.)
  * Element ID (`#theID`, `div#theID`, etc.)
  * Class name (`.theClass`, `p.theClass`, etc.)
* Basic DOM manipulation
  * `document.querySelector`/`document.querySelectorAll`
  * `.textContent`/`.innerHTML`
* Developer console
  * `console.log`
  * `console.group/.groupEnd/.groupCollapsed`
* Basic [event](https://www.w3schools.com/js/js_events.asp) handling
  * `onsubmit`
  * Anonymous functions
  * `.preventDefault`
  * `.target`
* Template strings
  * String interpolation, _e.g._ `` `Hi, ${name}` ``
  * Multi-line strings
* Emmet abbreviations for code editors ([syntax reference](https://docs.emmet.io/abbreviations/syntax/))

## DOM Manipulation
{{< code html >}}
&lt;div class=&quot;person&quot;&gt;
  &lt;h2 id=&quot;firstName&quot;>Han&lt;/h2&gt;
  &lt;h2 id=&quot;lastName&quot;>Solo&lt;/h2&gt;
  &lt;p>Made the Kessel Run in less than 12 parsecs&lt;/p&gt;
  &lt;button>Click here to hire me!&lt;/button&gt;
&lt;/div&gt;
{{< /code >}}

{{< code js >}}
// Get all h2 elements with querySelectorAll. Returns a NodeList
const headings = document.querySelectorAll('.person h2')
console.log(headings) 
// => [h2#firstName, h2#lastName]

// Get a single element with querySelector
const heading = document.querySelector('.person h2')
console.log(heading)
// => h2#firstName

// Do something when a click event occurs
const button = document.querySelector('button')
button.onclick((ev) => {
  alert('clicked!')
  console.log(ev.target)
  // => button
})
{{< /code >}}

## Presentations
* <a target="_blank" href="/history-of-the-web.pdf">JavaScript History</a>
* <a target="_blank" href="/bootcamp-success.pdf">Bootcamp Expectations and Tips for Success</a>

## Links
* [Foundation CSS Framework](http://foundation.zurb.com)
* [Mozilla Developer Network (MDN)](https://developer.mozilla.org/en-US/) - An excellent documentation and learning resource for all your HTML/CSS/JS needs

## Projects

### People Factory
[Morning](https://github.com/xtbc17s1/people-factory/tree/3a7d947fa8b62fe6516a801db89bd2e0899a5385) | [Afternoon](https://github.com/xtbc17s1/people-factory/tree/9d9e368d4125a2a3a1af549eb299ac9ebfdfad88)

## Homework

Add form values to `.details` using `document.createElement` and `appendChild`, instead of `innerHTML`.

#### Bonus Credit
Break out some of this functionality into a separate function.

#### Super Mega Bonus Credit
Do not hard-code the names of the fields in your JavaScript. Loop over all the elements in the form.
