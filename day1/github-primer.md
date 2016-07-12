## Github Primer

### Cybersecurity First Principles
* __Domain Separation__: Good fences make good neighbors. When trying to secure a home or computer, separating the areas where resources are and people work prevents accidents and loss of data or private information. We are preventing the information worlds from colliding.

* __Modularization__: The concept of modularity is like building blocks. Each block (or module) can be put in or taken out from a bigger project. Each module has its own separate function that is interchangeable with other modules

* __Least Privilege__: One of the ways to protect information is by limiting what people can with your information and resources.

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
[Cyber security First Principle Reflections](#cyber-security-first-principle-reflections)  
[Additional Resources](#additional-resources)


### Step 1
First things first, create a free account on Github. https://github.com/join

[Top](#table-of-contents)

### Step 2
Complete the Github tutorial.
https://guides.github.com/activities/hello-world/

At the end of Step 2, you will have created a **Remote** repository. It is "remote" because all your files are in the Github cloud. How do you continue to work on your repository if you had no Internet connection? Also, it is not convenient to write and test code online. It would be great to your own **Local** repository. We will do just that in the next step.

[Top](#table-of-contents)

### Step 3
To create a **Local** repository there are two basic options.
1. Clone a remote repository on your computer, or
2. Initialize a new git repository from scratch on your computer.

[Top](#table-of-contents)

##### Clone a remote repository
Let's go with option #1. Git tools do not come pre-installed. To check if they exist on your operating system, open up a command line interface and type `git`. If git is installed, this command will give you some help options. If the command is not recognized, then use this link to install git for your operating system flavor. https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

For a Ubuntu Desktop OS that you created in the `Virtualization` module, here are the instructions to type in a terminal:

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

> We do not need to use this option currently, so you may move to [Step 4](#step-4)

For option #2, navigate to the folder with your files. Then use the init command: `git init`. That's it!

[Top](#table-of-contents)

### Step 4
In this step we will make changes to files in our Local repository and then `push` changes back to the remote repository.

Git is based on a "de-centralized" model. Which means that there is no central authoritative repository. Every repository, Local or Remote, is fully autonomous and fully functional on its own. So changes made in any repository are tracked in that repository only. Two repositories do not communicate unless there is a explicit request to synchronize changes across them. This will make more sense as we work through a scenario.

Let's open the hello-world folder in the Ubuntu Desktop OS VM and make changes to the `README.md` file in a text editor.

![readme](../img/primer/clonedrepo.png)

![readme](../img/primer/openreadme.png)

![readme](../img/primer/editfile.png)

Now check the status of the local repository. Make sure you navigate to a folder within your repository in the terminal first. These commands will help you do both these actions.

```
cd hello-world
git status
```

![gitstatus](../img/primer/gitstatus.png)

A few things to notice here.
* `On branch master`: You are on the master branch in your local repository.
* `Your branch is up-to-date with 'origin/master'` Your local repository master branch is in sync with your remote repository master brach on Github. The default name for the remote repository is **origin**.
* `Changes not staged for commit:` git follows a two step process to save changes to a repository. First the user indicates which modified/deleted/new files need to be _staged_ for a save in the repository. Second these staged files are _committed_ to the repository. We will look at commands to do both of these shortly.
* `modified:   README.md`: git knows that the README.md file has been modified

Now we stage our changes for a commit using `git add --all` command. Then we check the status of the repository again.

![gitadd](../img/primer/gitadd.png)

This time the modified files are staged for a commit and appear in green.

Now before we commit/save these files into our repository. We want to make sure that the author details in your Ubuntu Desktop OS VM are configured. Keep them the same as your details on Github.com. Use the following commands to set these for all your local repositories.

![gitconfig](../img/primer/gitconfig.png)

You can check your updates by using the `--list` option.

![gitconfiglist](../img/primer/gitconfiglist.png)

You only have to set the config parameters once. Now that they are set, git will keep reusing them when making commits or merging your changes with other repositories.

Now let's commit the changes that we staged before. Here we use the `commit` option with `-m` to provide a short commit message. This helps us remember various checkpoints in our editing process. These messages are very helpful to rollback changes to an appropriate commit.

![gitcommit](../img/primer/gitcommit.png)

`git status` now reports no uncommitted changes. But it indicates that `Your branch is ahead of 'origin/master' by 1 commit`. Which means that our local repository master branch is more recent commits than the remote repository master branch.

To push our local commits to the remote repository, we need the git `push` command. With this command we need to indicate the name of the remote repository followed by the name of the local repository branch that has updates to be pushed.

#### Questions
What is the default name of the remote repository?  
What is the name of the main branch in our local repository?

To push local commits to the remote repository, here is the command we will use `git push origin master`

![gitpush](../img/primer/gitpush.png)

Here is the status of the local repository. Nothing to commit. up-to-date.

![gitpush](../img/primer/gitstatuspush.png)

If you visit your remote repository your changes will be reflected there. You should also see your commit message there.

![updateremote](../img/primer/remoteupdate.png)

git version control is very efficient for text files. It does not store entire files for old versions but only the differences. So it is prudent to make frequent commits. Then push these changes to the remote repository.

[Top](#table-of-contents)

### Step 5
What happens if we make some changes to README.md on Github.com? How do we get these changes back into our local repository. We will learn just that in this step.

I realized that I forgot to add a link to UNO's Cybersecurity programs in the README.md file. So I will go ahead and do that and commit those changes online.
Click on README.md file on Github and click the edit option.

#### Edit mode
![githubedit](../img/primer/githubedit.png)

#### Make changes and commit
![githubcommit](../img/primer/githubcommit.png)

#### See changes
![githubupdated](../img/primer/githubupdated.png)

Now the remote repository is one commit ahead of my local repository. To bring the local repository up to speed, we use the `git pull` command.

![gitpull](../img/primer/gitpull.png)

Now if we see our local README.MD file, it should have the updated link.

![localpullupdate](../img/primer/localpullupdate.png)

At this point you know enough to keep both the local and remote repositories synchronized.

[Top](#table-of-contents)

### Step 6
Forking a repository. This is as easy as pie. But what is a fork and what do you use it for?

Here is what Github [says](https://help.github.com/articles/fork-a-repo/):
> A fork is a copy of a repository. Forking a repository allows you to freely experiment with changes without affecting the original project.

> Most commonly, forks are used to either propose changes to someone else's project or to use someone else's project as a starting point for your own idea.

> Every public repository can be forked

So head-on over to a hello-world repository developed by one of your peers. Then click the "Fork" button.

![githubfork](../img/primer/githubfork.png)

Now you will have your very own copy of your peer's repository to work on. Using Step 3 you can clone this repository to your local computer. Make changes to files and push it back to this forked remote repository. You may also make direct changes to it on Github itself (Step 5).

[Top](#table-of-contents)

### Step 7
In this step we make changes to the fork of your peers' repository and create a pull request.

Let's assume that a `gencyber` user forks `robinagandhi/hello-world` repository.

![forkedrepo](../img/primer/forkedrepo.png)

The gencyber user now makes changes to the README.md file in this forked repository. She is also the owner of this forked repository.

![forkupdate](../img/primer/forkupdate.png)

To suggest these changes to `robinagandhi`; `gencyber` user has to create a pull request. So `gencyber` user switches over to the Pull Request tab and clicks the pull request button.

![forkpulltab](../img/primer/forkpulltab.png)

Here is a open pull request that compares the master branches across the two repositories.

![forkpullopen](../img/primer/forkpullopen.png)

`robinagandhi` user is now notified of a pull request on his hello-world repository.
He examines the suggested changes, and in this case the files can be automatically merged.

![forkmerge](../img/primer/forkmerge.png)

In cases where files cannot be merged automatically, discussions around the pull request can help to resolve the conflicts manually. In this case that won't be necessary. With a few more simple clicks the changes are merged.

![mergeconfirm](../img/primer/mergeconfirm.png)

Confirmation message after a successful merge.

![mergemsg](../img/primer/mergemsg.png)

The updated content is now reflected in `robinagandhi/hello-world` repository.

![finalupdate](../img/primer/forkupdatefinal.png)

And that is how you collaborate using Github.

[Top](#table-of-contents)

### Step 8
To communicate and write on Github, it is useful to learn Markdown and its Github Flavor Variants. https://help.github.com/categories/writing-on-github/


You are now ready to explore the wonderful world of open source on Github. Enjoy and make your own contributions!

[Top](#table-of-contents)

### Cyber security First Principle Reflections

On Github, only the `owner` of a remote repository can push commits to it. All other `Github users` have the limited privilege to make a pull request. The repository owner reviews pull requests and initiates a merge action. The owner may reject pull requests if not seen appropriate. A `collaborator` can push commits, but cannot delete a repository or add other collaborators. These constrains show the concept of _least privilege_ with github user roles. Users should have no more privilege than that required for their job.

Developers often design Github repositories, to be self contained _modules_. These modules are then put in or taken out of a bigger project. During build time these components are composed to create an integrated system. This strategy facilitates __Modularization__. Following this principle allows globally distributed teams to collaborate and locate faulty components.

Finally, Github repositories separate source code from other resources. This separation allows longterm archival and maintenance of a codebase, separate from its dependencies. _Domain Separation_ allows managing source code versions for different products and operating environments.

[Top](#table-of-contents)

## Additional Resources

* Creating a local repository first and then adding a remote repository, [Github](https://try.github.io/)
* [Github cheatsheet](https://services.github.com/kit/downloads/github-git-cheat-sheet.pdf)
* Collection of [Github tutorials](https://help.github.com/articles/good-resources-for-learning-git-and-github/)

[Top](#table-of-contents)

## Special Thanks

* A special thanks to Matt Hale, Aaron Vigal and Cade Wollcot for reviews of this module and thoughtful discussions.

[Top](#table-of-contents)

#### License
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">Cybersecurity Modules</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://faculty.ist.unomaha.edu/rgandhi/" property="cc:attributionName" rel="cc:attributionURL">Robin Gandhi</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.
