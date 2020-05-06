# Learning Notes - GIT & GITHUB

`Learning Resources for DevOps, SRE, Cloud & Engineering Management`

[![BINPIPE](https://img.shields.io/badge/BINPIPE-YouTube-red)](https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A)
[![Learn DevOps!](https://img.shields.io/badge/BINPIPE-Learn--DevOps-orange)](https://github.com/BINPIPE/resources/blob/master/devops-lesson-plans.md)

## [![BINPIPE](https://img.shields.io/badge/Live--Classroom-blue)](https://forms.gle/tDJxDyj2nJyfsgsk7)

**Git** is a distributed version control system.

A Version Control System is a system which maintains different versions of your project when we work in a team or as an individual. (system managing changes to files) As the project progresses, new features get added to it. So, a version control system maintains all your different versions of your project for you and you can rollback to any version you want without causing any trouble to you for maintaining different versions by giving names to it like MyProject, MyProjectWithFeature1, MyProjectWithFeatureN and so on.

**Distributed Version Control System** means every collaborator(any developer working on a team project)has a local repository of the project in his/her local machine unlike central where team members should have an internet connection to update their work to the main central repository.

So, by distributed we mean : project is distributed. A repository is an area which keeps all your project files, images, etc.

**Git Repository Structure**

It consists of 4 parts:

1.  Working directory : This is your local directory where you make the project (write code) and make changes to it.

2.  Staging Area (or index) : this is an area where you first need to put your project before committing. This is used for code review by other team members.

3.  Local Repository : this is your local repository where you commit changes to the  
    project before pushing them to the central repository on Github. This is what is provided by the distributed version control system. This corresponds to the .git folder in our directory.

4.  Central Repository : This is the main project on the central server, a copy of which  
    is with every team member as a local repository.

All the repository structure is internal to Git and are transparent to developer.

**Common GIT Operations**

## **checkout a repository from github**

Create a working copy of a local repository by running the command  

`# git clone /path/to/repository`  

when using a remote server, your command will be  

`# git clone username@host:/path/to/repository`

## **add & commit**

You can propose changes (add it to the Index) using  

`# git add <filename>`  

`# git add *`  

This is the first step in the basic git workflow. To actually commit these changes use  

`# git commit -m "Commit message"`  

Now the file is committed to the HEAD, but not in your remote repository yet.

## **pushing changes**

Your changes are now in the HEAD of your local working copy. To send those changes to your remote repository, execute
`# git push origin master`
Change master to whatever branch you want to push your changes to.

If you have not cloned an existing repository and want to connect your repository to a remote server, you need to add it with  

`# git remote add origin <server>`  

Now you are able to push your changes to the selected remote server

## **create a new repository**

create a new directory, open it and perform a  

`# git init`  

to create a new git repository.

## **Some commands which relate to repository structure:**

    git add
    // transfers your project from working directory to staging area.

    git commit
    // transfers your project from staging area to Local Repository.

    git push
    // transfers project from local to central repository. (requires internet)

## **Code snippet for automation**

    #EAZYGIT
    function eazygit() {
        git add .
        git commit -a -m "$1"
        git push
    }

## **branching**

Branches are used to develop features isolated from each other.
The master branch is the "default" branch when you create a repository.
Use other branches for development and merge them back to the master branch upon completion.

create a new branch named "feature_x" and switch to it using  

`# git checkout -b feature_x`  

switch back to master  

`# git checkout master`  

and delete the branch again  

`# git branch -d feature_x`  

a branch is not available to others unless you push the branch to your remote repository  

`# git push origin <branch>`  



## **update & merge**

to update your local repository to the newest commit, execute  

`# git pull`  

in your working directory to fetch and merge remote changes.  

To merge another branch into your active branch (e.g. master), use  

`# git merge <branch>`  

in both cases git tries to auto-merge changes. Unfortunately, this is not always possible and results in conflicts. You are responsible to merge those conflicts manually by editing the files shown by git. After changing, you need to mark them as merged with  

`# git add <filename>`  

before merging changes, you can also preview them by using  

`# git diff <source_branch> <target_branch>`  


## **Another way to branch:**

`git rebase myBranch`  


This merges the branch with master in a serial fashion.

Now,
`git push origin master`  


Contributing to open source by : fork a project and do some work (add new features) in your branch and then do a pull request on github.

**Accessing github central repository via Https or ssh**

Here, transfer project means transfer changes as git is very lightweight and works on changes in project. It internally does the transfer by using Lossless Compression Techniques and transferring compressed files. Https is the default way to access github central repository.

**by git remote add origin http_url :**
remote means the remote central repository.
origin corresponds to your central repository
which you need to define (here by giving https 
url) in order to push changes to github.

**Via SSH:** connect to Linux or other servers remotely.

If you access github by ssh you don’t need to type your username and password everytime you push changes to github.

**Terminal commands :**

    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    This does the ssh key generation using RSA cryptographic algorithm.

    eval "$(ssh-agent -s)" -> enable information about local login session.

    ssh-add ~/.ssh/id_rsa -> add to ssh key.
    cat ~/.ssh/id_rsa (use .pub file if not able to connect)
    add this ssh key to github.  

    Now, go to github settings -> new ssh key -> create key

    ssh -T git@github.com -> activate ssh key (test connection)

Refresh your github Page after doing the above.

<pre>
<a href="https://www.binpipe.org">BINPIPE</a> aims to simplify learning for those who are looking to make a foothold in the industry. 
Write to me at <b>nixgurus@gmail.com</b> if you are looking for tailor-made training sessions. 
For self-study resources look around in this repository, <a href="https://www.binpipe.org/">the Binpipe Blog</a> and <a href="https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A">Youtube Channel</a>.
</pre>

* * *

:ledger: Maintainer: **[Prasanjit Singh](https://www.linkedin.com/in/prasanjit-singh)** \| **www.binpipe.org**

* * *

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
