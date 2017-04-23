+++
date = "2016-06-10T23:02:52-04:00"
next = "/setup-mac/git"
prev = "/setup-mac/editor"
title = "Terminal"
toc = true
weight = 3

+++

{{% h %}}
<i class="fa fa-terminal"></i> terminal
{{% /h %}}

You'll be using a terminal app throughout the setup process, as well as in class.

macOS comes with **Terminal.app**, which you can find at `/Applications/Utilities/Terminal.app` or by searching for _Terminal_ in Spotlight. It will do the job just fine, but if you're interesting in dressing it up or exploring other shells, read on.

![Terminal.app](/images/terminal-icon.png)

**[iTerm2](https://www.iterm2.com/index.html)** is a popular alternative to Terminal.app. It's free and includes some advanced features that the built-in Terminal lacks. Personally, I've been using **[Hyper](https://hyper.is/)** for about a month. Hyper is written in JavaScript, HTML, and CSS and is cross-platform, which is particularly appealing for class.

Whichever you choose, you'll use it frequently enough that I recommend keeping it in your Dock.

{{% aside info "$ _" %}}
When you launch your terminal, it will (by default) run a UNIX shell called Bash. Bash will present a command prompt, indicated by `$`. We'll generally prefix terminal commands with that symbol in our documentation. You're not meant to type the `$` character, and it won't be included if you copy and paste the commands from this site.
{{% /aside %}}

## Zsh

I am a big fan of Zsh ("Z shell"), which is an alternative to Bash. Even better is **[Oh My Zsh](http://ohmyz.sh/)**, which is a framework for managing Zsh configuration. I love it. You'll still use Terminal.app, iTerm2, or Hyper to launch your shell, but it will run Zsh in place of Bash.

I will be using Zsh (with Oh My Zsh) in class, but most of what we'll do works just as well in Bash.

{{% aside info "Command Line Power User" %}}
If you're not very familiar with UNIX shells, or if you'd like to learn some cool tricks, including Oh My ZSH features, sign up for Wes Bos's free **[Command Line Power User](http://commandlinepoweruser.com/)** videos. (They're all on YouTube, but signing up for the email makes it a little easier to find them.)
{{% /aside %}}
