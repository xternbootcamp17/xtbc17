+++
date = "2016-06-10T23:06:12-04:00"
next = "/setup-windows/terminal"
prev = "/setup-windows/editor"
title = "Git"
toc = true
weight = 3

+++

{{% h "git-logo.svg" %}} for Windows{{% /h %}}

Git is a distributed version control system. (But you knew that already, because you totally completed a [Git tutorial](/prereqs/git/)---_right_?)

There are several ways to go about making Git usable on Windows, but my favorite is to install the aptly-named **[Git for Windows](https://git-for-windows.github.io/)**. The great thing about Git for Windows is that it comes with **Git Bash**---a UNIX-style shell.

{{% download "Git for Windows" "https://git-for-windows.github.io/" %}}

{{% aside danger "Get the right Git" %}}
Please note that this is **not** the same Git for Windows that you'll find on git-scm.com.
{{% /aside %}}

{{% aside info "GitHub Desktop" github-alt %}}
**[GitHub Desktop](https://desktop.github.com/)** is a very nice, free graphical interface for Git. Although we'll use Git from the command-line a great deal, we'll also look at how GitHub Desktop can make certain tasks easier.
{{% /aside %}}

## Git Setup Options

You'll have a few choices to make during the setup process.

**Adjusting your PATH environment**:
The second option is probably best: _Use Git from the Windows Command Prompt_. With this option, you'll be able to use Git commands from the regular Windows command line, should you choose to.

<div class="img git-win-01-path"><span>Choose <strong>Use Git from the Windows Command Prompt</strong></span></div>

**Choosing HTTPS transport backend**:
Select the first option: _Use the OpenSSL library_.

<div class="img git-win-02-https"><span>Choose <strong>Use the OpenSSL library</strong></span></div>

**Configuring the line ending conversions**:
Select the second option: _Checkout as-is, commit Unix-style line endings_.

<div class="img git-win-03-line-endings"><span>Choose <strong>Checkout as-is, commit Unix-style line endings</strong></span></div>

**Configuring the terminal emulator to use with Git Bash**:
You'll install a different terminal emulator shortly, so your choice here is inconsequential. Just go with the first option: _Use MinTTY (the default terminal of MSYS2)_.

<div class="img git-win-04-terminal"><span>Choose <strong>Use MinTTY (the default terminal of MSYS2)</strong></span></div>

**Configuring extra options**:
The defaults here are fine.

<div class="img git-win-05-extras"><span>Leave the default selections on.</span></div>

## Configuring Git

Next, tell Git what name and email address it should use to sign code that you've authored. While you're at it, tell it to use Code as the editor. Setup should have created a **Git Bash** shortcut. Launch Git Bash, and enter the following commands, substituting your actual name and email address:

{{< term os="windows" >}}
git config --global user.name "Your Full Name"
git config --global user.email "youremailaddress@example.com"
git config --global core.editor "code --wait"
{{< /term >}}

{{% aside info "$ _" %}}
Git Bash will present a command prompt, indicated by `$`. We'll generally prefix terminal commands with that symbol in our documentation. You're not meant to type the `$` character, and it won't be included if you copy and paste the commands from this site.
{{% /aside %}}