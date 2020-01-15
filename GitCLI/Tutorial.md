# Git Command Line Tutorial


## Table of Contents

1. [ Dependencies ](#desc)
2. [ Usage ](#usage)
3. [ Common Errors ](#errors)
4. [ LFS ](#lfs)
5. [ Branching Strategies ](#branching)


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
[image]()
3. Use vim editor as git's standard(or if you prefer something else, go for it, I just use vim) and click next
4. If you want git to be usable from cmd, chose that option, otherwise go for standard. (I only use git from bash - Fark-I)
[image]()
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
[image]()

5. You can check if the remote url has been added and it is correct by typing ``git remote -v``

If all is in order continue to step 6, otherwise see the [ Common Errors ](#errors)

6. Now we will need to track the files from the local directory. 
  !!! Warning, if you have any files in the remote repository, first you need to type``git pull``, in order to "download" it, this applies
  to readme.md files too. 

To track local files you type ``git add .`` - this will track all local files

7. Next we will need to commit these files by ``git commit -m "your message here"`` (you need the " " after the -m) - this will add 
a commit message, which will be visible on github.com, it is important for this message to be self-explanatory, brief but containing 
information necessary to identify what has changed since the last update/message(example: "add trees")

8. When all these steps are done, we need to "upload" to github.com by ``git push -u origin master`` - this commands contents and meaning:
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

### Version Control

#### Tracking changes

#### Pushing changes to remote

<a name="errors"></a>
## 3. Common Errors

### Merge conflict

<a name="lfs"></a>
## 4. Git Large File Storage(LFS)

<a name="branching"></a>
## 5. Branching Strategies


