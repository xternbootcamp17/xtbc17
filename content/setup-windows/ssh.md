+++
date = "2016-06-10T23:40:37-04:00"
next = "/setup-windows/github"
prev = "/setup-windows/node"
title = "SSH"
toc = true
weight = 6

+++

{{% h %}}
<i class="fa fa-terminal"></i> ssh
{{% /h %}}

We recommend setting up an SSH key to simplify authentication with GitHub and other services.

## Check for an existing key

**In Hyper, make sure you're in your home directory.** You will be by default, but you can double-check with the "print working directory" command: `pwd`

{{< term output="2" os="windows" >}}
pwd
/c/Users/dstrus
{{< /term >}}

You should be in `/c/Users/yourusername`. If not, you can switch to that directory with the `cd` command, passing in the directory you want to switch to.

{{< term os="windows">}}
cd ~
{{< /term >}}

{{% aside tip "~" %}}
You can always use a tilde `~` as a shortcut for your home directory.
{{% /aside %}}

**Check for an `.ssh` directory:**

{{< term output="2" os="windows" >}}
ls .ssh
{{< /term >}}

If you see an `id_rsa.pub` file, then you already have an SSH key and can skip to the next page.

## Generate an SSH key

Type the following command to generate your SSH key, substituting the same email address you used for Git earlier:

{{< term os="windows" >}}
ssh-keygen -t rsa -C "youremail@example.com"
{{< /term >}}

It should prompt you for a file name. Hit 'enter' to accept the default.

It will then prompt you for a password. You can hit 'enter' (twice) to not set a passphrase. That compromises your key should anyone gain access to your laptop, but it may be simpler for the sake of this course. When you truly want to maximize security, it's much safer to create a passphrase when generating a key.

If all is well, you should see that your identification and your public key have been saved to `.ssh/id_rsa` and `.ssh/id_rsa.pub` respectively.

You'll test your new key shortly, but first you'll need to create a GitHub account and add your public key to the account.
