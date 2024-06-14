# Setup

The following document will walk through setting up a **git** environment.

## Install Git

Download and install [**git**](https://git-scm.com/). The only settings that I tend to modify from the default are:

* Use Visual Studio Code as git's default editor. VS Code must be installed for this option to work.
* Override the default branch name to `main`. This will align git with GitHub's default behavior.

Verify git installation as follows:

```pwsh
C:\> git --version
git version 2.45.2.windows.1
```

## Configure SSH

The instructions that follow were adapted from [Generating a new SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) and [Add a new SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).

Execute the following from a PowerShell terminal:

```pwsh
# should be your @army.mil email
C:\> ssh-keygen -t ed25519 -C "your_email@example.com"
```

You'll see the following output:

```
Generating public/private ed25519 key pair.
Enter file in which to save the key ($env:userprofile/.ssh/id_ed25519):
```

You can name the SSH key file anything you want, but I would recommend keeping it stored at `$env:userprofile/.ssh`. It's useful to provide descriptive names in the event that you have an environment with multiple SSH profiles. For instance, I have both a personal GitHub account as well as my GitHub Enterprise account for work. I have mine setup as:

* `home_ed25519`
* `work_ed25519`

After specifying the filename, you will be prompted to enter a passphrase:

```
Enter passphrase (empty for no passphrase):
```

After entering the passphrase, you will be prompted to confirm the passphrase:

```
Enter same passphrase again:
```

After confirming the passphrase, you should see the following output (note that your randomart will be different):

```
Your identification has been saved in C:/Users/user/.ssh/docs_ed25519
Your public key has been saved in C:/Users/user/.ssh/docs_ed25519.pub
The key fingerprint is:
SHA256:Yhf....................................... your_email@example.com
The key's randomart image is:
+--[ED25519 256]--+
|  ...            |
| o = . o         |
|o Z + * .        |
| O B B . .       |
|  X X E S        |
| o @.* o         |
|  C D*.          |
|   =.o*          |
|    +=           |
+----[SHA256]-----+
```

### Add SSH key to ssh-agent

Open an **Administrative** PowerShell terminal and run the following:

```pwsh
Get-Service -Name ssh-agent | Set-Service -StartupType Automatic
Start-Service ssh-agent

# replace with your ssh key
ssh-add C:/Users/user/.ssh/docs_ed25519
```

### Add SSH key to GitHub Account

From a PowerShell terminal, copy the contents of the SSH public key to the clipboard:

```pwsh
# replace with your ssh key
cat C:/Users/user/.ssh/docs_ed25519.pub | clip
```

After logging into GitHub, navigate to the [**SSH and GPG keys**](https://github.com/settings/keys) settings page:

![ssh-and-gpg-keys](https://github.com/JaimeStill/JaimeStill/assets/14102723/48ec346e-4d28-4d3c-984c-2b8351f4a673)

Click the **New SSH Key** button.

In the *Add new SSH Key* form, provide a descriptive **Title**, keep the **Key type** set to *Authentication Key* and paste your key into the **Key** textbox:

![new-ssh-key](https://github.com/JaimeStill/JaimeStill/assets/14102723/1248bb52-b64c-427b-8414-4ccf65d019f7)

Click **Add SSH key**.

You will see the key added to your **SSH keys** section:

![ssh-key-added](https://github.com/JaimeStill/JaimeStill/assets/14102723/528db871-49db-48ae-b5c9-2698e4061781)

In order to use the SSH key, you will need to configure *Single Sign On* for the organization. Click the **Configure SSO** drop-down:

![sso-auth](https://github.com/JaimeStill/JaimeStill/assets/14102723/a03060ab-d6c6-4eca-bd7c-2e442d881930)

Click the **Authorize** button and follow the auth flow. Once complete, you should see the option for **Configure SSO** change to *Deauthorize*:

![sso-deauth](https://github.com/JaimeStill/JaimeStill/assets/14102723/7aeb054a-74c3-4356-8435-bbc174d3fff1)

## Configure Multiple SSH Accounts

If you have both personal and work GitHub accounts that use SSH, you will need to setup an SSH configuration that can differentiate which key to use based on the host. Create a config file by running the following in a PowerShell terminal:

```pwsh
New-Item $env:USERPROFILE\.ssh\config -ItemType File
```

Open the file in VS Code:

```pwsh
code $env:USERPROFILE\.ssh\config
```

Configure the default GitHub host to use your personal SSH key, and a work GitHub host to use your work SSH key:

> You can setup HOST however you like, but HostName and User should not be changed.

```config
# Default GitHub
HOST github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/home_ed25519

HOST work.github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/work_ed25519
```

## Test Setup

You can verify your setup by cloning a repository using the work SSH key. Navigate to a repository within your organization, click the **Code** dropdown. Under the **Local** tab, make sure *SSH* is selected and click the copy icon to the right of the URL:

![repo-to-clone](https://github.com/JaimeStill/JaimeStill/assets/14102723/ad555ce3-53e7-4f25-b7e1-7cbd01a62d74)

Open a PowerShell terminal pointed to the location you want to clone the repository. Type `git clone` then paste the SSH URL from the repository. Change `@github.com` to the host designation specified in your SSH config, i.e. `@work.github.com`.

The following is an example of the full command execution:

```pwsh
C:\> git clone git@work.github.com:s2va/monorepo-planning.git
Cloning into 'monorepo-planning'...
remote: Enumerating objects: 1343, done.
remote: Counting objects: 100% (708/708), done.
remote: Compressing objects: 100% (427/427), done.
remote: Total 1343 (delta 292), reused 566 (delta 232), pack-reused 635
Receiving objects: 100% (1343/1343), 11.00 MiB | 10.21 MiB/s, done.
Resolving deltas: 100% (543/543), done.
```