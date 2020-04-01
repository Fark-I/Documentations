# Git Command Line Tutorial


## Table of Contents

1. [ Dependencies ](#desc)
2. [ Usage ](#usage)
3. [ Common Errors ](#errors)
4. [ LFS ](#lfs)
5. [ Branching Strategies ](#branching)
6. [Good Practices/Useful Commands](#commands)
7. [Ignoring Files with .gitignore](#ignore)


## Introduction 

Git is a distributed version-control system for tracking changes in source code during software development. 
It is designed for coordinating work among programmers, but it can be used to track changes in any set of files. 
Its goals include speed, data integrity, and support for distributed, non-linear workflows.

<a name="desc"></a>
## 1. Dependencies

### Git Bash

#### Windows

[ Git Bash ](https://gitforwindows.org/) is a bash emulation with the purpose of making the cmd behave just like it does on
UNIX or Linux system 

##### Download and Install 

1. [Download](https://gitforwindows.org/) Git Bash from the link and click on the .exe that you have downloaded.
2. Select the following dependencies at least
![image](https://github.com/Fark-I/Documentations/blob/master/GitCLI/images/Installation1.png)
3. Use vim editor as git's standard(or if you prefer something else, go for it, I just use vim) and click next
4. If you want git to be usable from cmd, chose that option, otherwise go for standard. (I only use git from bash - Fark-I)
![image](https://github.com/Fark-I/Documentations/blob/master/GitCLI/images/Installation2.png)
5. Use OpenSSL library, click next
6. Checkout Windows-style option, and click next
7. Use MinTTY and click next
8. Enable all options, click next.
9. Install



#### Linux/Unix(Mac)

Not neccessary to install anything, since git commands are executable in the cmd on these operating systems

<a name="usage"></a>
## 2. Usage

This section describes how to use git, pushing-pulling, cloning and other operations.

### Creating a repository

If no repository was created for the project you are working on, you can create a new repository on GitHub under our 
[ Organization ](https://github.com/Virsabi)

#### Adding an existing project 

This section describes how to add an existing project to a github repository. For example if you have a project under D:/Unity/Projects
in order to "upload" it to git, you are going to have to follow these steps.

!! Make sure there is a repository on github first !!

1. Navigate to the project directory in file explorer (f.ex: D:/Unity/Projects/SampleProject/). 
2. Right-click and select "Git Bash here", this will open a bash window
3. Type `` git init `` , which will create a .git folder in the directory. It initializes a local git repository.
4. In order to have the local git repository connected to the one on GitHub, you will need to type `` git remote add origin *remote url*``
The remote URL is the link from the GitHub repository you have on github.com. Example see below.
![image](https://github.com/Fark-I/Documentations/blob/master/GitCLI/images/git_link.png)

5. You can check if the remote url has been added and it is correct by typing ``git remote -v``

If all is in order continue to step 6, otherwise see the [ Common Errors ](#errors)

6. Add a .gitignore file. For instructions, see [Ignoring Files with .gitignore](#ignore)

7. Now we will need to track the files from the local directory. 
  !!! Warning, if you have any files in the remote repository, first you need to type``git pull``, in order to "download" it, this
  applies to readme.md files too. 

  To track local files you type ``git add .`` - this will track all local files

8. Next we will need to commit these files by ``git commit -m "your message here"`` (you need the " " after the -m) - this will add 
a commit message, which will be visible on github.com, it is important for this message to be self-explanatory, brief but containing 
information necessary to identify what has changed since the last update/message(example: "add trees")

9. When all these steps are done, we need to "upload" to github.com by ``git push -u origin master`` - this commands contents and meaning:
- push: "upload"
- -u: sets the upstream
- origin: remote
- master: branch

Summary:
```
git init
git remote add origin *remote url*
git add .
git commit -m "Your message"
git push -u origin master
```


### Cloning a repository

Navigate to the project repository on github and find the link as seen in the image and copy it.

![image](https://github.com/Fark-I/Documentations/blob/master/GitCLI/images/git_link.png)

Once that is done, navigate to a folder on your computer, where you would like to "download" the project, right click and git bash here.

To clone the repo, type ``git clone *repository URL*``

### Pulling

Pulling essentially means to acquire the changes from the remote repository and merge them into your local.
(Remote -  the project repository on github.com)


!!! It is recommended that every time, before making any changes in the directory that you check if there are any changes on remote !!!

If you don't have any local changes you can simply type ``git pull`` and it will download all the changes on the remote

If you have changes, but you don't want to keep them, type ``git stash`` which will stash your changes, basically acts as a "revert" function

<a name="tracking"></a>
#### Tracking changes

Open gitbash in the local folder of your repository.

Type ``git status`` to see if you have any changes.

If it shows a lot of red text, don't be scared, that only means that your changes are not tracked.

To track changes type ``git add .`` (. <- means to track all changes in the current folder)

If you type ``git status`` again, you will see that the file names appear as green, that means your changes have been tracked.

As your changes have been added, make sure you add a message, describing your changes by ``git commit -m "YourMessageHere"``

To upload your changes, follow instructions under [ Pushing changes to remote ](#pushing)


<a name="pushing"></a>
#### Pushing changes to remote

Before you are able to push(upload) your changes, make sure you have followed the steps from [Tracking changes](#tracking) !

After you have described your changes by a commit message, you can type ``git push`` to push to the current branch that you are on.

<a name="errors"></a>
## 3. Common Errors

### Merge conflict

Solving a merge conflict can be difficult, if you are not very experienced with git, I recommend you to seek assistance from a member
of the Development team or Fark-I. 
If you are experienced, here are some useful commands:

```
git diff
git checkout --theirs
git checkout --ours
git reset --hard head

git cherry-pick [--edit] [-n] [-m parent-number] [-s] [-x] [--ff]
		  [-S[<keyid>]] <commit>
git cherry-pick (--continue | --skip | --abort | --quit)
```

<a name="lfs"></a>
## 4. Git Large File Storage(LFS)

1. Download and Install [Git LFS](https://git-lfs.github.com/)

``git lfs install``
You will need to run this in your repository directory, once per repository.

Select the file types you'd like Git LFS to manage (or directly edit your .gitattributes). You can configure additional file extensions at anytime.

``git lfs track "*.psd"``
Make sure .gitattributes is tracked

``git add .gitattributes``
There is no step three. Just commit and push to GitHub as you normally would.

```
git add file.psd
git commit -m "Add design file"
git push origin master
```

<a name="branching"></a>
## 5. Branching Strategies

Branching can be very important when working with multiple people on the same project and avoid conflicts.

[Here](https://nvie.com/posts/a-successful-git-branching-model/) is a good explanation on how it works, and why it is very useful.

- Useful commands

```
git checkout -b branchName   (create new branch)
git checkout branchName      (switch to branch named: branchName)
git branch -d branchName     (deletes branch named: branchName... !!! make sure to merge with another branch if you want to keep changes!!!!
```


<a name="commands"></a>
## 6. Good Practices/Useful Commands

First of all you need to make sure that the remote is not ahead (no changes in the remote compared to local) use ``git fetch`` to 
check if there were any changes in the remote.

``git status`` to check if you have any changes in the local 
``git checkout -b branchname`` create new branch

<a name="ignore"></a>
## 7. Ignoring files with .gitignore

.gitignore is a "text" file which you can edit to specify which folders should git not add/ignore when tracking files on local. You
should always create a .gitignore file before you call ``git add.``. 

You can either use one of the existing .gitignore files from previous projects or create a new one on [gitignore.io](https://www.gitignore.io)

If you change the gitignore file after you are tracking files in a local repository, you will need to clear the cache in order to untrack the files/folders that are specified in the gitignore. Follow the commands below to achieve this.

```
git rm . -r --cached
git add .
git commit -m "fixed gitignore"
```

###### Most Used Commands

```
git status
git pull
git add .
git commit -m "message"
git push
git init
git fetch
git checkout -b branchname
```
