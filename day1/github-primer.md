## Github Primer

Git is a popular developer tool for collaboration and version control. It is not limited to just code. You may use it for collaborative development of any written work. Github is a popular online platform to host public git repositories. There are several other services like Github, such as [BitBucket](https://bitbucket.org/). For our lessons we will stick to Github for now.  Working through the tutorials below, git's use for collaboration and version control will become clear.

### Table of Contents    
[Step 1: Create Account](#step-1)  
[Step 2: Hello World](#step-2)  
[Step 3: Clone Repository](#step-3)  
[Step 4: Push Changes](#step-4)  
[Step 5: Pull Remote Changes](#step-5)  
[Step 6: Fork Repository](#step-6)  
[Step 7: Pull Request](#step-7)  
[Step 8: Markdown](#step-8)  


### Step 1
First things first, create a free account on Github. https://github.com/join

### Step 2
Complete the Github tutorial.
https://guides.github.com/activities/hello-world/

At the end of Step 2, you have created a **Remote** repository. It is "remote" because all your files are in the Github cloud. How do you continue to work on your repository if you had no Internet connection? Also, it is not convenient to write and test code online. It would be great to your own **Local** repository. We will do just that in the next step.

### Step 3
To create a **Local** repository there are two basic options.
1. Clone a remote repository on your computer, or
2. Initialize a new git repository from scratch on your computer.

##### Clone a remote repository
Let's go with option #1. Git tools do not come pre-installed. To check if they exist on your operating system, open up a command line interface and type `git`. If git is installed, this command will give you some help options. If the command is not recognized, then use this link to install git for your operating system flavor. https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

For a Ubuntu OS, here are the instructions:

```bash
sudo apt-get update
sudo apt-get -y install git
```
The `-y` option automates the installation by responding YES to any prompts. After the installation succeeds, type `git` to see various command options. To clone a remote repository, we first need a reference to it. On Github.com, navigate to your hello-world repository and click on the button that says `Clone`. Copy that URL.

![clone](../img/primer/clonerepo.png)

Now we are ready to clone this remote repository, and create a local repository. To do this we will use the `git clone <repository URL>` command. In the command below replace the URL with the URL of the repository that you want to clone.

```bash
git clone https://github.com/robinagandhi/hello-world.git
```
The command may prompt for your Github username and password (for private repositories). You will start to see some download messages and upon success, your local repository will be ready for use. You may navigate to the corresponding file folder and confirm if all the files are there.

```bash
steal@ubuntu:~$ git clone https://github.com/robinagandhi/hello-world.git
Cloning into 'hello-world'...
Username for 'https://github.com': robinagandhi
Password for 'https://robinagandhi@github.com':
remote: Counting objects: 4, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (4/4), done.
Checking connectivity... done.
steal@ubuntu:~$ cd hello-world/
steal@ubuntu:~/hello-world$ ls
LICENSE  README.md
```

##### Initialize a new repository

For option #2, navigate to the folder with your files. Then use the init command: `git init`. That's it! We do not need to use this option currently, so let's move to [Step 4](#step-4)

### Step 4
In this step we will make changes to files in our Local repository and then `push` changes back to the remote repository.

Git is based on a "de-centralized" model. Which means that there is no central authoritative repository. Every repository, Local or Remote, is fully autonomous and fully functional on its own. So changes made in any repository are tracked in that repository only. Two repositories do not communicate unless there is a explicit request to synchronize changes across them. This will make more sense as we work through a scenario.

Let's open the hello-world folder on our local computer and make changes to the `README.md` file in a text editor.

![readme](../img/primer/editreadme.png)

Now check the status of our repository. Make sure you navigate to a folder within your repository in the terminal. Then issue this command `git status`.

![gitstatus](../img/primer/gitstatus.png)

A few things to notice here.
* `On branch master`: You are on the master branch in your local repository.
* `Your branch is up-to-date with 'origin/master'` Your local repository master branch is in sync with your remote repository master brach on Github. The default name for the remote repository is **origin**.
* `Changes not staged for commit:` git follows a two step process to save changes to a repository. First the user indicates which modified/deleted/new files need to be _staged_ for a save in the repository. Second these staged files are _committed_ to the repository. We will look at commands to do both of these shortly.
* `modified:   README.md`: git knows that the README.md file has been modified

Now we stage our changes for a commit using `git add --all` command. Then we check the status of the repository again.

![gitadd](../img/primer/gitadd.png)

This time the modified files are staged for a commit and appear in green.

Now before we commit/save these files into our repository. We want to make sure that the author details in your local computer are configured. Keep them the same as your details on Github.com. Use the following commands to set these for all your local repositories.

![gitconfig](../img/primer/gitconfig.png)

You can check your updates by using the `--list` option.

![gitconfiglist](../img/primer/gitconfiglist.png)

You only have to set the config parameters once. Now that they are set, git will keep reusing them when making commits or merging your changes with other repositories.

Now let's commit the changes that we staged before. Here we use the `commit` option with `-m` to provide a short commit message. This helps us remember various checkpoints in our editing process. These messages are very helpful to rollback changes to an appropriate commit.

![gitcommit](../img/primer/gitcommit.png)

`git status` now reports no uncommitted changes. But it indicates that `Your branch is ahead of 'origin/master' by 1 commit`. Which means that our local repository master branch is more recent commits than the remote repository master branch.

To push our local changes to the remote repository, we need the git push command. With this command we need to indicate the name of the remote repository followed by the name of the local repository branch that has updates to be pushed.

#### Questions
What is the default name of the remote repository?
What is the name of the main branch in our local repository?

Here is the command we will use `git push origin master`

![gitpush](../img/primer/gitpush.png)

Here is the status of the local repository. Nothing to commit. up-to-date.

![gitpush](../img/primer/gitstatuspush.png)

If you visit your remote repository your changes will be reflected there. You should also see your commit message there.

![updateremote](../img/primer/remoteupdate.png)

git version control is very efficient for text files. It does not store entire files for old versions but only the differences. So it is prudent to make frequent commits. Then push these changes to the remote repository.

### Step 5
Make remote changes and pull changes to local repository.

### Step 6
Forking a repository.

### Step 7
Make changes to your peers' repository create a pull request.

### Step 8
Learn Markdown and Github Flavor Variants. https://help.github.com/categories/writing-on-github/
