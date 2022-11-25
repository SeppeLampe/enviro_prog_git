# Git in Environmental Programming
This is a quick introduction to Git for IUPWARE programmers. 

**For this exercise, kindly get in the groups you formed for your projects. Only one person needs to make the remote repo for your group's project. You can call this person "Mr. Manager" (ladies too). Follow along as a group and make sure that everyone does the rest of the tutorial so you are all connected to your group's remote.**

## Setting up Git

### Make your account
Since you're already on GitHub, head to the top right of the webpage and make an account. Choose the free option.

### Download and install Git
Your account on GitHub lets you make public/remote repos for your work. However, you also want the ability to easily pipe your work from your local computer to remote repos hosted on GitHub. Therefore, install [Git bash](https://git-scm.com/downloads)

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
Generate an SSH key. This is unique to your machine/GitHub connection. It let's you connect and authenticate your local machine to the remote server on GitHub without having to give usernames/passwords.

You might already have keys, which should be in a hidden ".ssh" folder somewhere like "C:/Users/yourname/.ssh"

But you probably don't. So, open Git Bash and type this with your **GitHub email address** and ignore the name changes and password prompts by pressing the **Enter** key:
```
ssh-keygen -t rsa -b 4096 -C <your_github_email@something>
```

This produces a public/private key pair. The public key will have a ".pub" extension. Find your public key, open it and paste its contents in your GitHub account settings page under "SSH and GPG keys; New SSH key":
<p align="center">
<img src="https://github.com/lwilgrant/enviro_prog_git/blob/main/keys.PNG" />
</p>

Then, in Git Bash, establish this connection (type yes/press enter if it warns you):
```
ssh -T git @github.com
```

You have now created a connection between your local machine and your GitHub account. Now we're ready to start using Git.

## Using Git

### Create a remote repo
In order to practice with Git, you will need a remote repo for platforming work on GitHub. **Mr. Manager**, select your profile dropdown menu and "Your repositories", then create a repository. Don't worry about license and readme files. Then, head to your Settings and invite your group members with their GitHub usernames/emails under "Collaborators":
<p align="center">
<img src="https://github.com/lwilgrant/enviro_prog_git/blob/main/collabs.PNG" />
</p>

### Create a local repo
Go to the directory on your local machine where your projects are, i.e. "C:/Users/yourname/repos/", and make a repo with the same name as the remote above.

Initialize your local repo by opening Git Bash in its folder (right click some blank space in your file explorer in the directory of your local repo) and typing:
```
git init
```

This tells Git that your local folder is a Git repository. It will produce a hidden ".git" folder that tracks stuff. You only need to do this once per repo.

### Connect repos

As of now, we have made an SSH connection between your local machine and your GitHub account. We also made remote and local repos. However, Git doesn't yet know that the local and remote repos are lovers that build beautiful code babies. So you need to tell Git this by typing the following in Git Bash (opened in your local repo):
```
git remote add origin git@github.com:<username/yourrepo>
```

Note that the address used above can be found in your remote repo here:
<p align="center">
<img src="https://github.com/lwilgrant/enviro_prog_git/blob/main/connecting.PNG" />
</p>

### Exercise 1: Push

Ouuuuuuu weeee!
<p align="center">
<img src="https://github.com/lwilgrant/enviro_prog_git/blob/main/Mr_poopy_butthole.webp" />
</p>

We're so close! We have GitHub accounts, Git Bash, **intimately** connected local and remote repos. Now we need to make some dummy code and push it from our local to remote repos. 

As a group exercise, I want every group member to open up a blank text file called "myfavprof.txt" using MS notebook or your python editor. This is of course your code that you hope to back up on the remote, so the file should be in your local repo. Simply type the first name of the best professor in IUPWARE. For one person at a time, I want each group member to push their not-so-secret code containing their favorite professor to the remote. After doing this, I want you to check the commit history of your remote repo to see how this process is incredibly valuable to collaborative coding.

Checking the status of your repo:
```
git status
```

Add your code to the staging area:
```
git add myfavprof.txt
```

Commit the code, which confirms the state of your files in the local repo and preps them for moving to the remote. Here you add some comment in quotation marks that should be brief but descriptive of what you did to the code:
```
git commit -m "My favorite professor updated in the very public code"
```

Finally, push the code to your remote! This tells Git to push the committed changes to the remote repo specified by "origin" (the one you connected above) on the branch "master". Normally, your default branch is labelled "main". We don't have time to get into branches, and you probably don't need them.
```
git push origin main
```

Now check your commit history to have an overview of the acitivty in your remote:
<p align="center">
<img src="https://github.com/lwilgrant/enviro_prog_git/blob/main/commits.PNG" />
</p>

You can also check your commit history in Git Bash:
```
git log
```

### Exercise 2: Pull

Imagine your group's Mr. Manager has already pushed a bunch of new things to your remote repo, but you have been quietly delegating your time to the Surface Water Hydrology report instead of working on your coding project, which might not be the best strategy for organizing your efforts... You're now in a pickle; your local repo is behind the remote.

No worries! You can easily catch up to Mr. Manager in your local repo by "**pulling**" the changes on the remote:
```
git pull origin main
```

### Exercise 3: Revert

But what if your Mr. Manager srcrewed up? He/she pushed some garbage that broke the matrix. Yet, **conveniently**, Mr. Manager was doing frequent commits of his/her work, thereby allowing you to track their stupid changes.

Again, in Git bash, you can view the labels or ids for each commit in your commit history with:
```
git log
```

For one of my projects, commit ids look like the following (circled in red):
<p align="center">
<img src="https://github.com/lwilgrant/enviro_prog_git/blob/main/revert.PNG" />
</p>

Imagine one of your group members screwed up. **After you have all pulled changes from the remote, organize for one person** in your group to revert a commit.

If you want to revert the last commit, this is simple:
```
git revert HEAD
```

If you want to revert an earlier commit, use its id:
```
git revert <commit_id>
```

# That's everything! Got Git it!

