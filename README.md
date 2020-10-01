# Introduction to git and its commands

Git

[Git](https://git-scm.com/) is a command-line tool that will help us with version control in several different ways:

Allowing us to keep track of changes we make to our code by saving snapshots of our code at a given point in time.

![](https://cdn-images-1.medium.com/max/2800/0*tcomhX7pzhocCwD4)

Allowing us to easily synchronize code between different people working on the same project by allowing multiple people to pull information from and push information to a repository stored on the web.

![](https://cdn-images-1.medium.com/max/2800/0*niLmRbLxFC5E_XH8)

Allowing us to make changes to and test out code on a different *branch* without altering our main codebase, and then merging the two together.

Allowing us to revert back to earlier versions of our code if we realize weΓÇÖve made a mistake.

In the above explanations, we used the word repository, which we havenΓÇÖt explained yet. A Git repository is a file location where weΓÇÖll store all of the files related to a given project. These can either be remote (stored online) or local (stored on your computer).

## GitHub

[GitHub](https://www.github.com/) is a website that allows us to store Git repositories remotely on the web.

LetΓÇÖs get started by creating a new repository online

1. Make sure that you have a GitHub account set up. If you donΓÇÖt have one yet, you can make one [here](https://github.com/join?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home).

1. Click the + in the top-right corner, and then click ΓÇ£New repositoryΓÇ¥

1. Create a repository name that describes your project

1. (Optional) Provide a description for your repository

1. Choose whether the repository should be public (visible to anyone on the web) or private (visible just to you and others you specifically grant access)

1. (Optional) Decide whether you want to add a README, which is a file describing your new repository.

![](https://cdn-images-1.medium.com/max/2800/0*pR_nYBPmSeU8EXtN)

* Once we have a repository, weΓÇÖll probably want to add some files to it. In order to do this, weΓÇÖll take our newly created *remote* repository and create a copy, or clone, of it as a *local* repository on our computer.

1. Make sure you have git installed on your computer by typing git into your terminal. If it is not installed, you can download it [here](https://git-scm.com/downloads).

1. Click the green ΓÇ£Clone or DownloadΓÇ¥ button on your repositoryΓÇÖs page, and copy the URL that pops down. If you didnΓÇÖt create a README, this link will appear near the top of the page in the ΓÇ£Quick SetupΓÇ¥ section.

![](https://cdn-images-1.medium.com/max/2800/0*TMgQiOCa2bmiUl3K)

1. In your terminal, run git clone <repository url>. This will download the repository to your computer. If you didnΓÇÖt create a README, you will get the warning: You appear to have cloned into an empty repository. This is normal, and thereΓÇÖs no need to worry about it.

![](https://cdn-images-1.medium.com/max/2744/0*9_zgEYA0Fi4f5cG7)

1. Run ls, which is a command that lists all files and folders in your current directory. You should see the name of the repository youΓÇÖve just cloned.

1. Run cd <repository name> to change directory into that folder.

1. Run touch <new file name> to create a new file in that folder. You can now make edits to that file. Alternatively, you can open the folder in your text editor and manually add new files.

1. Now, to let Git know that it should be keeping track of the new file youΓÇÖve made, Run git add <new file name> to track that specific file, or git add . to track all files within that directory.

![](https://cdn-images-1.medium.com/max/2292/0*bG-hme19lDgj554l)

## Commits

* Now, weΓÇÖll start to get into what Git can be really useful for. After making some changes to a file, we can *commit* those changes, taking a snapshot of the current state of our code. To do this, we run: git commit -m ΓÇ£some messageΓÇ¥ where the message describes the changes you just made.

* After this change, we can run git status to see how our code compares to the code on the remote repository

* When weΓÇÖre ready to publish our local commits to Github, we can run git push. Now, when we go to GitHub in our web browser, our changes will be reflected.

* If youΓÇÖve only changed existing files and not created new ones, instead of using git add . and then git commitΓÇª, we can condense this into one command: git commit -am ΓÇ£some messageΓÇ¥. This command will commit all the changes that you made.

* Sometimes, the remote repository on GitHub will be more up to date than the local version. In this case, you want to first commit any changes, and then run git pull to pull any remote changes to your repository.

## Merge Conflicts

* One problem that can emerge when working with Git, especially when youΓÇÖre collaborating with other people, is something called a merge conflict. A merge conflict occurs when two people attempt to change a file in ways that conflict with each other.

* This will typically occur when you either git push or git pull. When this happens, Git will automatically change the file into a format that clearly outlines what the conflict is. HereΓÇÖs an example where the same line was added in two different ways:

a **=** 1

**<<<<<** HEAD

b **=** 2

**=====**

b **=** 0

**>>>>>** 56782736387980937883

c **=** 3

d **=** 4

e **=** 5

* In the above example, you added the line b = 2 and another person wrote b = 3, and now we must choose one of those to keep. The long number is a *hash* that represents the commit that is conflicting with your edits. Many text editors will also provide highlighting and simple options such as ΓÇ£accept currentΓÇ¥ or ΓÇ£accept incomingΓÇ¥ that save you the time of deleting the added lines above.

* Another potentially useful git command is git log, which gives you a history of all of your commits on that repository.

![](https://cdn-images-1.medium.com/max/2800/0*5YA8uP1oCbK4RGKP)

Potentially even more helpful, if you realize that youΓÇÖve made a mistake, you can revert back to a previous commit using the command git reset in one of two ways:

* **git reset ΓÇö hard <commit> :**reverts your code to exactly how it was after the specific commit. To specify the commit, use the commit hash associated with a commit which can be found using git log as shown above.

* **git reset ΓÇö hard origin/master :** reverts your code to the version currently stored online on Github.

## Branching

After youΓÇÖve been working on a project for some time, you may decide that you want to add an additional feature. At the moment, we may just commit changes to this new feature as shown in the graphic below

![](https://cdn-images-1.medium.com/max/2800/0*QJkTMYoIoywjms-g)

But this could become problematic if we then discover a bug in our original code, and want to revert back without changing the new feature. This is where branching can become really useful.

Branching is a method of moving into a new direction when creating a new feature, and only combining this new feature with the main part of your code, or the main branch, once youΓÇÖre finished. This workflow will look more like the below graphic:

![](https://cdn-images-1.medium.com/max/2800/0*0md2P5f5dFyYj5LB)

The branch you are currently looking at is determined by the HEAD, which points to one of the two branches. By default, the HEAD is pointed at the master branch, but we can check out other branches as well.

Now, letΓÇÖs get into how we implement branching in our git repositories:

1. Run git branch to see which branch youΓÇÖre currently working on, which will have an asterisk to the left of its name.

![](https://cdn-images-1.medium.com/max/2800/0*FTocmCPFKitMC9w0)

1. To make a new branch, weΓÇÖll run git checkout -b <new branch name>

![](https://cdn-images-1.medium.com/max/NaN/1*b31hiO4ynbDLRrXWEFF4aQ.png)

1. Switch between branches using the command git checkout <branch name> and commit any changes to each branch.

1. When weΓÇÖre ready to merge our two branches together, weΓÇÖll check out the branch we wish to keep (almost always the master branch) and then run the command git merge <other branch name>. This will be treated similarly to a push or pull, and merge conflicts may appear.

## More GitHub Features

There are some useful features specific to GitHub that can help when youΓÇÖre working on a project:

* Forking: As a GitHub user, you can *fork* any repository that you have access to, which creates a copy of the repository that you are the owner of. We do this by clicking the ΓÇ£ForkΓÇ¥ button in the top-right.

* Pull Requests: Once youΓÇÖve forked a repository and made some changes to your version, you may want to request that those changes be added to the main version of the repository. For example, if you wanted to add a new feature to Bootstrap, you could fork the repository, make some changes, and then submit a pull request. This pull request could then be evaluated and possibly accepted by the people who run the Bootstrap repository. This process of people making a few edits and then requesting that they be merged into a main repository is vital for what is known as *open-source software*, or software that is created by contributions from several developers.

* GitHub Pages: GitHub Pages is a simple way to publish a static site to the web. (WeΓÇÖll learn later about static vs dynamic sites.) To do this:

1. Create a new GitHub repository.

1. Clone the repository and make changes locally, making sure to include an index.html file which will be the landing page for your website.

1. Push those changes to GitHub.

1. Navigate to the Settings page of your repository, scroll down to GitHub Pages, and choose the master branch in the dropdown menu.

2. Scroll back down to the GitHub Pages part of the settings page, and after a few minutes, you should see a notification that ΓÇ£Your site is published at: ΓÇªΓÇ¥ including a URL where you can find your site!

# Learning Git

[Git LFS](https://github.com/git-lfs/git-lfs/wiki/Tutorial)


