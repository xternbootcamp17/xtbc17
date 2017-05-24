+++
date = "2017-05-17T13:54:51-04:00"
title = "Day 3: Megaroster"
toc = true
weight = 3
prev="/week1/day2"
next="/week1/day4"

+++

<date>Wednesday, May 17, 2017</date>

## Lecture Videos

Morning:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [Day 3, part 1](https://www.youtube.com/watch?v=FpmyQ-Cet6o&index=4&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F) | [2](https://www.youtube.com/watch?v=p9T-YJISXHY&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=5) | [3](https://www.youtube.com/watch?v=whGokpO6Wpw&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=6) | [4](https://www.youtube.com/watch?v=Iv_OFDB_-Oc&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=7) | [5](https://www.youtube.com/watch?v=uAnBpVRmCzo&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=8) | [6](https://www.youtube.com/watch?v=tF8s6DemQ7M&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=9) | [7](https://www.youtube.com/watch?v=q5qx7KgjY0E&list=PLuT2TqJuwaY_bcdBTgaK3S8VrN_6POv5F&index=10)

Afternoon:

* [Full Playlist](https://www.youtube.com/playlist?list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [Day 3, part 1](https://www.youtube.com/watch?v=wOYPD1Upfh4&index=4&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [2](https://www.youtube.com/watch?v=cw7aB9rTuds&index=5&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [3](https://www.youtube.com/watch?v=I1eF0wpsPWw&index=6&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [4](https://www.youtube.com/watch?v=P_L7KjyrYjs&index=7&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [5](https://www.youtube.com/watch?v=dEwP0rvy2V4&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=8) | [6](https://www.youtube.com/watch?v=NHB3Es3BaAs&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=9) | [7](https://www.youtube.com/watch?v=IK2w9t2ImLU&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=10) | [8](https://www.youtube.com/watch?v=RbMg_GDexyY&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=11) | [9](https://www.youtube.com/watch?v=NQwpPBYw4DI&index=12&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [10](https://www.youtube.com/watch?v=-iZulyiSGBs&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=13) | [11](https://www.youtube.com/watch?v=fmEcK_vy1_Y&index=14&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG) | [12](https://www.youtube.com/watch?v=uConk-khS0Q&list=PLuT2TqJuwaY8syQZ9ERbc2gtX_v1m2xqG&index=15)

## Topics

### Git
* Starting a new repository
* Adding a remote repository (like Github)
* Seeing what changed with `git diff`
* Forking and cloning repositories

### Foundation

* The grid system
* Responsive design (adjusting style based on window size)
* [Foundation Docs](http://foundation.zurb.com/sites/docs/)

### Functions as methods

* Methods calling methods (_e.g._ `megaRoster.addChild` calls `this.buildListItem`)
* Binding: Manually setting the value of `this` with `.bind`

### DOM Manipulation

* [parentElement](https://developer.mozilla.org/en-US/docs/Web/API/Node/parentElement)
* [childNodes](https://developer.mozilla.org/en-US/docs/Web/API/Node/childNodes)
* [firstChild](https://developer.mozilla.org/en-US/docs/Web/API/Node/firstChild)
* [firstElementChild](https://developer.mozilla.org/en-US/docs/Web/API/ParentNode/firstElementChild)
* [insertBefore](https://developer.mozilla.org/en-US/docs/Web/API/Node/insertBefore)
* [closest](https://developer.mozilla.org/en-US/docs/Web/API/Element/closest) (experimental)

## Examples

### Git

#### Starting a new project with a git repository

First make a new directory and then navigate into the new directory.  Then start a new repository with `git init`.

{{< term >}}
mkdir my_new_project
cd my_new_project
git init
{{< /term >}}

To be able to make our first commit, we need to first add something to our empty project folder.  A common first choice is a `README.md` file, which is a document written in [markdown](https://guides.github.com/features/mastering-markdown/) that provides information about the project.

{{< term >}}
echo "# My New Project" >> README.md
git add .
git commit -m "Initial commit"
{{< /term >}}

Once we have our first commit, we can add a 'remote' for our repository, like [github](https://github.com) or [bitbucket](https://bitbucket.org/).  For github, log in to github.com, then hit the '+' button in the top right of the screen to add a new repository.  Then, it will give you the following commands to run from the command line.

{{< term >}}
git remote add origin git@github.com:myusername/my_new_project.git
git push -u origin master
{{< /term >}}

This adds the github remote as 'origin' and sets it as the default for when you push your changes.  From this point forward, just type `git push` to push your changes to the remote.

#### Forking a Repo

Making your own copy of an existing repo is called [forking](https://guides.github.com/activities/forking/).  Unlike a cloned copy, which retains the permissions set by the original owner, a forked copy now belongs to you (meaning you can make any changes you want to it).

Just hit the 'Fork' button in the upper right of the repo page, and this will add a copy to your personal github.

<div class="img github-fork-repo"><span>Hit the 'Fork' button in the upper right of the repo page, and this will add a copy to your personal github.</span></div>

### Foundation

Foundation is a CSS (and JS) framework that makes it easy to create stylish, responsive web pages.  The foundation (get it?) of it is the [grid system](http://foundation.zurb.com/grid.html).  The grid splits the page into 12 equally-sized columns, making it easy to set the alignment of elements on the page by specifying how many columns they span.

In addition, you can add sizes of 'small', 'medium', 'large', etc, to specify different behavior at different screen sizes.  In the following example, the two child divs will be full screen width at small screen sizes (stacked on top of each other), and half of the screen width at medium and larger screen sizes (appearing next to each other).

{{< code html >}}
&lt;div class=&quot;row&quot;&gt;
  &lt;div class=&quot;small-12 medium-6 columns&quot;&gt;
  &lt;/div&gt;
  &lt;div class=&quot;small-12 medium-6 columns&quot;&gt;
  &lt;/div&gt;
&lt;/div&gt;
{{< /code >}}

### Manually setting `this` with `bind`

In JavaScript, the value of `this` in any function depends on the context in which the method was called.  For example, if a function is an event listener callback, `this` will be set to the target that caused the event to fire.  Sometimes, this is not the `this` we want. Luckily, JavaScript also has the `.bind` method, which allows a function to be 'bound' to a particular value of `this`.

{{< code js >}}
this.x = 9        // here, 'this' is the global window object

const module = {
  x: 81,
  getX: function() {
    return this.x
  }
}

module.getX()     // 81
// getX was called on module, so 'this' is module and this.x is 81

const retrieveX = module.getX
retrieveX()       // 9
// retrieveX is a const declared in the global scope, so 'this' is window

const boundGetX = retrieveX.bind(module)
boundGetX()       // 81
// by binding to module, 'this' will always be set to module for boundGetX
{{< /code >}}

## Presentations

* [Review: Objects and Functions](/03-review-objects-and-functions.pdf)

## Projects

### Megaroster

[Morning](https://github.com/xtbc17s1/megaroster/tree/d733ad2186e75deb8331b0c2d39736595379d1bd) | [Afternoon](https://github.com/xtbc17s1/megaroster/tree/a725906dec243ea053d75822cfd1621a8d555909)

These are links directly to the repo as of the commits where we left off today. Even after we add more commits tomorrow, these links will still point to this point in time.

## Homework

Finish yesterday's homework, using my Megaroster ([morning](https://github.com/xtbc17s1/megaroster/tree/d733ad2186e75deb8331b0c2d39736595379d1bd) | [afternoon](https://github.com/xtbc17s1/megaroster/tree/a725906dec243ea053d75822cfd1621a8d555909)) as a base. Don't forget to keep the `students` array in sync with the DOM.

### Bonus Credit

Fool around with Foundation and/or CSS to make it look nicer.

### Mega Bonus Credit

Add buttons to change the position of the student within the list. In other words, add "Move Up" and "Move Down" buttons.

### Super Mega Bonus Credit

Persist the student data using `window.localStorage`.
