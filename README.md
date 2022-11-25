# Git in Environmental Programming
This is a quick introduction to Git for IUPWARE programmers. 

## Setting up Git

### Make your account
Since you're already on GitHub, head to the top right of the webpage and make an account. Choose the free option.

### Download and install Git
Your account online lets you make public/remote repos for your work. However, you also want the ability to easily pipe your work from your local computer to the remote repo. Therefore, install [Git bash](https://git-scm.com/downloads)

The default installation preferences are mostly fine, **except** that you should deviate and follow this selection for handling line endings:

<p align="center">
<img width="400" src="https://github.com/lwilgrant/enviro_prog_git/blob/main/install_option.png" />
</p>

### Configure Git
Open **Git Bash** and type:
```
git config --global user.name <your name>
git config --global user.email <your_email@something>
```

### Create a secure connection between Git and your local machine
Generate an SSH key. This is unique to your machine/GitHub connection. It let's you connect and authenticate to the remote server on GitHub without having to give usernames/passwords.

You might already have keys, which should be in a hidden ".ssh" folder somewhere like "C:/Users/yourname/.ssh"

But you probably don't. So type this with your **GitHub email address** and ignore the name changes and password prompts by pressing the **Enter** key:
```
ssh-keygen -t rsa -b 4096 -C <your_github_email@something>
```
This produces a public/private key pair. The public key will have a ".pub" extension. Find your public key, open it and paste its contents in your GitHub account settings page under "SSH and GPG keys; New SSH key":
<p align="center">
<img src="https://github.com/lwilgrant/enviro_prog_git/blob/main/install_option.png" />
</p>
