+++
date = "2016-06-10T23:06:12-04:00"
next = "/setup-windows/ssh"
prev = "/setup-windows/terminal"
title = "Node.js"
toc = true
weight = 5

+++

{{% h "node-logo.svg" /%}}

## Installation

To install Node.js, click one of the big, green download links on the web site.

{{% download "Node.js" "http://nodejs.org/" %}}

{{% aside info Note %}}
Node version numbers are confusing, but either the LTS version (6.10.2 as of this writing) or the Current version (7.9.0) will do for our purposes.
{{% /aside %}}

## Testing your installation

After Node is installed, close Hyper and reopen it. That way, `node` and other related commands will be available to you from any folder. Test your installation by running the following command:

{{< term os="windows" >}}
npm install -g create-react-app
{{< /term >}}

You should see a progress bar of sorts while packages download and, eventually, a tree structure of various package names and version numbers. As you may have guessed, aside from testing your Node installation, this has the side effect of installing `create-react-app`, which we'll later use to do exactly what its name suggests.

## Yarn

[Yarn](https://yarnpkg.com/) is an alternative to NPM that offers several advantages&mdash;not the least of which is speed.

[Download the installer](https://yarnpkg.com/en/docs/install#windows-tab) from the Yarn site, and run it.

## Testing Yarn

Once Yarn is installed, run this command to test it:

{{< term os="windows" >}}
yarn global add eslint
{{< /term >}}
