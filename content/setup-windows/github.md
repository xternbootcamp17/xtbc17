+++
date = "2016-06-10T23:31:46-04:00"
prev = "/setup-windows/ssh"
title = "GitHub"
toc = true
weight = 7

+++

{{% h "github-logo.svg" /%}}


## Create a free GitHub account

GitHub is a service for storing your code in the cloud. It's wonderful for collaboration.

[Sign up for GitHub](https://github.com/join?source=header-home) using the same email address you used when creating your SSH key and your Git configuration.

<div class="img github-create-account"><span>Enter your info, and hit the green "Create an account" button.</span></div>

On the next screen, you'll see information about GitHub's free and paid plans. To finish creating a free account, just hit the green "Continue" button.

<div class="img github-choose-plan"><span>Hit the green "Continue" button.</span></div>

The next screen includes a survey. You're welcome to hit the "skip this step" link.

{{% aside tip "Verify your email address" %}}
GitHub will send you an email after you sign up. Click the link in the email to verify that the address belongs to you.
{{% /aside %}}

## Add your public key to your GitHub account

To send and receive code between your laptop and GitHub securely, you'll need to add your public SSH key to your GitHub account. **Never copy your private key to another machine unless you are absolutely sure what you're doing.**

Open your public key in Code with the following command:

{{< term os="windows" >}}
code .ssh/id_rsa.pub
{{< /term >}}

In Code, select all (`Ctrl A`) to highlight the contents of the file, and copy the selection to the clipboard (`Ctrl C`).

Now go to GitHub settings to add your public key to your account.

<div class="img github-settings"><span>Choose <em>Settings</em> from the user menu in the upper-right of your GitHub page.</span></div>

Choose "SSH and GPG Keys" from the left menu, then click "New SSH key" on the right.

<div class="img github-ssh-settings"><span>Click the button to add an SSH key to your account.</span></div>

Give your SSH Key a title (something to identify the machine on which the key was generated, such as "Surface Book"), and then paste in the contents that you copied from the terminal.

<div class="img github-new-ssh-key"><span>Paste in the contents of your public key.</span></div>

## Test your SSH key with your GitHub account

Return to Terminal and type the following command:

{{< term output="2,3,4" os="windows" >}}
ssh -T git@github.com
The authenticity of host 'github.com (192.30.255.112)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)?
{{< /term >}}

Go ahead and type `yes`.

{{< term output="1,2" os="windows" >}}
Warning: Permanently added 'github.com,192.30.255.112' (RSA) to the list of known hosts.
Hi dstrus! You've successfully authenticated, but GitHub does not provide shell access.
{{< /term >}}

If you see a message like the one above, you're ready to go!

## If you have trouble...

If that didn't work, your SSH keys may not have been generated with the correct file permissions, so run these two commands from your home directory (`~`):

{{< term os="windows" >}}
chmod -R 700 .ssh/
chmod 600 .ssh/id_rsa
{{< /term >}}
