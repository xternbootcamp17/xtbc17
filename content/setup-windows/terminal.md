+++
date = "2016-06-10T23:02:52-04:00"
next = "/setup-windows/node"
prev = "/setup-windows/git"
title = "Terminal"
toc = true
weight = 4

+++

{{% h %}}
<i class="fa fa-terminal"></i> terminal
{{% /h %}}

You'll be using the command line a fair amount in class. We'll be demonstrating everything on macOS, which is UNIX-based. Now that you've installed Git Bash, you too have a UNIX-like shell and can run the same commands.

As noted during setup, Git Bash can run in the default `cmd.exe` terminal, but it also comes with MinTTY. If you're on Windows 10, `cmd.exe` isn't quite the inexcusable piece of crap that it used to be. At least the dang window is resizable now---that only took 25 @#$% years! It's still a bit of pain though, and MinTTY has problems of its own. So let's not use either one! 

## Hyper

Although it isn't strictly required, I highly recommend installing **[Hyper](https://hyper.is/)**. It's a terminal client written in JavaScript, HTML, and CSS---and it's cross-platform! In fact, I'll be using the Mac version of Hyper in class.

Aside from being what I use, Hyper is much easier to use and to customize than `cmd.exe`, and it doesn't have MinTTY's issues with running native Windows apps.

{{% download Hyper "https://hyper.is/" %}}

## Configuring Hyper to Run Bash

Now we need to configure Hyper to run Git Bash when it starts. To do so, let's edit its configuration file. Launch **Git Bash** (_not_ Hyper!), and run the following command:

{{< term os="windows" >}}
code ~/.hyper.js
{{< /term >}}

We need to change two settings: _shell_ and _shellArgs_. Look for this section of the file, and make the changes shown on the highlighted lines:

{{< code lang="js" line="6,10" >}}
    // the shell to run when spawning a new session (i.e. /usr/local/bin/fish)
    // if left empty, your system's login shell will be used by default
    // make sure to use a full path if the binary name doesn't work
    // (e.g `C:\\Windows\\System32\\bash.exe` instead of just `bash.exe`)
    // if you're using powershell, make sure to remove the `--login` below
    shell: 'C:\\Program Files\\Git\\git-cmd.exe',

    // for setting shell arguments (i.e. for using interactive shellArgs: ['-i'])
    // by default ['--login'] will be used
    shellArgs: ['--command=usr/bin/bash.exe', '-l', '-i'],
{{< /code >}}

With that saved, you can quit Git Bash, and run Hyper, which will actually be running the Git Bash shell now. If you want to tweak more settings you can now run the `code ~/.hyper.js` command from Hyper. Feel free to poke around the preferences file for anything else you'd like to tweak, such as font size.

## Environment Variables

Things still aren't set up quite the way we want. Certain commands won't work quite right without another tweak, and we'd like to set Visual Studio Code as the default editor. Set a couple of environment variables by issuing the following command:

{{< term >}}
echo -e "export TERM=cygwin\nexport EDITOR=code\n" > .bash_profile
{{< /term >}}

This creates the file `.bash_profile` in your home directory, with the following contents:

{{< code lang="bash" class="line-numbers" label=".bash_profile" >}}
export TERM=cygwin
export EDITOR=code

{{< /code >}}