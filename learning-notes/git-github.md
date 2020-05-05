# Learning Notes - GIT & GITHUB 

`Learning Resources for DevOps, SRE, Cloud & Engineering Management`

[![BINPIPE](https://img.shields.io/badge/BINPIPE-YouTube-red)](https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A)
[![Learn DevOps!](https://img.shields.io/badge/BINPIPE-Learn--DevOps-orange)](https://github.com/BINPIPE/resources/blob/master/devops-lesson-plans.md)
[![BINPIPE](https://img.shields.io/badge/Live--Classroom-blue)](https://forms.gle/tDJxDyj2nJyfsgsk7)
---


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

**Some commands which relate to repository structure:**
```
git add
// transfers your project from working directory to staging area.

git commit
// transfers your project from staging area to Local Repository.

git push
// transfers project from local to central repository. (requires internet)
```
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
```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
This does the ssh key generation using RSA cryptographic algorithm.

eval "$(ssh-agent -s)" -> enable information about local login session.

ssh-add ~/.ssh/id_rsa -> add to ssh key.
cat ~/.ssh/id_rsa (use .pub file if not able to connect)
add this ssh key to github.  

Now, go to github settings -> new ssh key -> create key

ssh -T git@github.com -> activate ssh key (test connection)
```
Refresh your github Page.

**Working with git – Important Git commands**

-   **Git user configuration (First Step)**
    ```
    git --version (to check git version)
    git config --global user.name "your name here"
    git config --global user.email "your email here"
    ```
    These are the information attached to commits.
    
-   **Initialize directory :**
    
    `git init `
    initializes your directory to work with git and
    makes a local repository. .git folder is made
    
    OR
    
    `git clone http_url`
    This is done if we have an existing git repository.
    
-   **Connecting to repository :**
    
    `git remote add origin http_url/ssh_url`
    connect to central repo to push/pull
    
    pull means transferring the changes on central repository to your local repository. push is the vice versa of pull.
    
   `git pull origin master`
    Always first pull contents from central repo before pushing so that you are updated with other team members work. Here, master means the master branch (in Git).
    
-   **Steps to add a file to central Repository:**  
    First your file is in your working directory, Move it to the staging area by typing:
    
    `git add -A (for all files and folders)`
    
    `git status` : here, untracked files means files which you haven’t added to the staging area. Changes not staged for commit means you have staged the file earlier then you have made changes in that files in your working directory and the changes need to be staged once more.  
    Changes ready to be committed : these are files which have been committed and ready to be pushed to central repository.
    
    `git commit -a -m "message for commit"`
    -a : commit all files and for files which have been 
         staged earlier need not to be git add once more
    -a options does that automatically.
    
    `git push origin master` -> pushes your files to 
                             github master branch
    `git push origin anyOtherBranch` -> pushes any 
                          other branch to github.
    `git log` ; to see all your commits
    
    `git checkout commitObject(first 8 bits) file.txt`-> 
    revert back to this previous commit  for file file.txt
    
    commitObject can be seen via git log.
    HEAD -> pointer to our latest commit.
    

**Branching in Git**

create branch ->
`git branch myBranch`
or
`git checkout -b myBranch` -> make and switch to the 
                                  branch myBranch

Do the work in your branch. Then,
`git checkout master` ; to switch back to master branch

Now,  merge contents with your myBranch By:
`git merge myBranch` (writing in master branch)
This merger makes a new commit.

**Another way:**

`git rebase myBranch`

This merges the branch with master in a serial fashion.

Now,
`git push origin master`

Contributing to open source by : fork a project and do some work (add new features) in your branch and then do a pull request on github.



<pre>
<a href="https://www.binpipe.org">BINPIPE</a> aims to simplify learning for those who are looking to make a foothold in the industry. 
Write to me at <b>nixgurus@gmail.com</b> if you are looking for tailor-made training sessions. 
For self-study resources look around in this repository, <a href="https://www.binpipe.org/">the Binpipe Blog</a> and <a href="https://www.youtube.com/channel/UCPTgt4Wo0MAnuzNEEZlk90A">Youtube Channel</a>.
</pre>

___
:ledger: Maintainer: **[Prasanjit Singh](https://www.linkedin.com/in/prasanjit-singh)** | **www.binpipe.org**
___

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
