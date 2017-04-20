+++
date = "2016-06-10T23:06:12-04:00"
next = "/setup-mac/editor"
prev = "/setup-mac/git"
title = "Node.js"
toc = true
weight = 4

+++

{{% h "node-logo.svg" /%}}

## Installation
If you installed Homebrew in the previous step, use it to install Node.js:

{{< term >}}
brew install node
{{< /term >}}

If not, you can click one of the big, green download links on the Node.js web site.

### [Download Node.js](http://nodejs.org/)

{{% aside info Note %}}
Node version numbers are confusing, but either the LTS version (6.10.2 as of this writing) or the Current version (7.9.0) will so for our puposes.
{{% /aside %}}

## Testing your installation

After Node is installed, test your installation by running the following command:

{{< term >}}
npm install -g create-react-app
{{< /term >}}

You should see a progress bar of sorts while packages download and, eventually, a tree structure of various package names and version numbers. As you may have guessed, aside from testing your Node installation, this has the side effect of installing `create-react-app`, which we'll later use to do exactly what its name suggests.

{{% aside tip %}}
If the `npm` command isn't available, open a new tab in your terminal and try again. Opening a new tab should make `node` and other related commands available to you from any directory, if they weren't already.
{{% /aside %}}
