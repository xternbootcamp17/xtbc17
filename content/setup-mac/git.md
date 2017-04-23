+++
date = "2016-06-10T23:06:12-04:00"
next = "/setup-mac/node"
prev = "/setup-mac/terminal"
title = "Git"
toc = true
weight = 4

+++

{{% h "git-logo.svg" /%}}

Git is a distributed version control system. (But you knew that already, because you totally completed a [Git tutorial](/prereqs/git/)---_right_?) If you have previously installed Xcode and its command-line tools, you may already have Git installed. Find out by entering the following command:

{{< term output="2,4" >}}
git --version
git version 2.12.2
{{< /term >}}

If you see something like `git version 2.12.2`, then you already have Git. If not, skip to the next section to install Homebrew. If you have Git, but the version number is lower than 2.12.2 (as of April 11, 2017), then your version of Git is out of date. Continue to the next step to install Homebrew.

If your Git version is up-to-date, skip to the [Git Configuration](#configuring-git) section.

{{% aside info "GitHub Desktop" github-alt %}}
**[GitHub Desktop](https://desktop.github.com/)** is a very nice, free graphical interface for Git. Although we'll use Git from the command-line a great deal, we'll also look at how GitHub Desktop can make certain tasks easier.
{{% /aside %}}

## Homebrew

**[Homebrew](http://brew.sh)** is a package manager for macOS. That is, it manages the installation of certain software---especially UNIX tools---and the installed versions of that software.

Install Homebrew with the following command:

{{< term >}}
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
{{< /term >}}

## Installing Git with Homebrew

If you do not have Git installed at all, or if your version is out of date, run the following command to install the latest version:

{{< term >}}
brew install git
{{< /term >}}

Now check your Git version again.

{{< term >}}
git --version
{{< /term >}}

You should see an up-to-date version number.

The next time a new version of Git is released, just type the following commands:

{{< term >}}
brew update           # This updates Homebrew so it knows about the latest versions.
brew upgrade git      # This upgrades Git itself.
{{< /term >}}

## Configuring Git

Next, tell Git what name and email address it should use to sign code that you've authored. While you're at it, tell it to use Code as the editor. Enter the following commands, substituting your actual name and email address:

{{< term >}}
git config --global user.name "Your Full Name"
git config --global user.email "youremailaddress@example.com"
git config --global core.editor "code --wait"
{{< /term >}}
