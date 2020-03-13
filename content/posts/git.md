---
title: "Git: Version Control System"
date: 2020-01-04T04:32:54-06:00
tags: [Git, VCS]
featured_image: "/images/github-octocat.png"
description: "An overview and tutorial of how to utilize version control in your day-to-day development."
draft: false
---

# What is Version Control

Version control is a tool used to collaborate between people working on a codebase. The most popular version control system (VCS) tool is called Git. We will look into how Git has made open source collaboration easier and how to use this useful tool.

![alt text](/images/git.png)

# Background

Git was originally developed in 2005 by Linus Torvalds, the creator of Linux. Before those days, a lot of development teams would pass files around through email, floppy disks, and archived files. There was a system called CVS that had been an usage since the 1980s, but it was not ideal for sharing large projects between many developers. In 2002, Linus and his team decided to use a VCS called BitKeeper. BitKeeper is a "distributed system, whereby whole repositories [can] be forked and merged easily." However, being that this was a proprietary piece of software the Linux developers were held to restrictions as they were only interested in the free license. After abandoning BitKeeper and not finding a suitable VCS, Linus put his Linux work on hold to build his own VCS called Git. Some features of BitKeeper are present in Git such as fork, merge, and rebase.

# Terminology & Syntax

***repository (repo)*** - your project and all of its folders and files

***master*** - the repo's main branch that the production ready code lives

***remote*** - the central server of your repository, i.e. Github, BitBucket

***clone*** - to copy an existing git repo to your local workstation

***commit*** - to submit changes and new files to the existing repository

***fetch/pull*** - brings in the latest changes that do not exist locally; pull executes a combined fetch and merge function

***push*** - to submit the latest commits to the remote repository

***SHA*** - Every commit or node in the Git tree has a unique SHA key which can be used as an id to perform further operations

***head*** - a reference to the node where your repo currently points to

## Commonly used Commands

`git pull` - pulls in changes from the remote repository

`git add .` - stages changed files to be committed

`git commit` - commits files to the local repo

`git push` - sends the newly changed files to the remote repo

## The three states of Git

There are three main states that your files can reside in:

1. **Committed** is the state when none of your files differ from what is currently stored in the local repo. 
2. **Modified** is the state where the file has been changed but has not yet been staged.
3. **Staged** is the state at which the file has been indexed and will go into the next commit snapshot.

# What's a branch?

A branch is a divergent line of work that can continue without disrupting the master branch. Think of it as a tree with many different branches with many different shapes and sizes. Some branches are short-lived and are pruned after they are done serving their purpose, while other branches live on so long that they begin to become problems if they ever need to merge back into the master branch.

 ![alt text](/images/git-branches-merge.png)

 Many different types of Git workflows have developed over the years for dealing with large collaborative teams working on the same code base. In a feature branch workflow, a developer checks out to a new branch and names it whatever the feature is dealing with. After making a few commits, they are finished working on that feature and are ready to bring this new feature code back to the master branch where it can soon go to production. At this point, it may be beneficial to have another developer look over the code. This is where pull requests and code reviews come into play. 
 
 A pull request is a mechanism for a developer to notify team members that they have completed a feature. 
 
  ![alt text](/images/pull-request.png)
 
 A code review is conducted by another developer on the team to ensure that the feature worked on is using best practices and there are no glaring mistakes. I've found code reviews to be a great way to share context amongst the team and teach others. After the pull request is approved it is time to merge the feature branch into master.

# Creating a new repository

> Navigate to your favorite Git hosting site. For this example, I will be using Github. 

<small>NOTE: You must have an account. It's free to sign up.</small>

![alt text](/images/new_repo.png)

> Click on `New reposistory` in the upper-right hand corner

![alt text](/images/create_repo.png)

> Fill in the form fields

> Check the box for Initializing the repo with a README (documentation is important for any project!)

Now it's time to link the local project to this remote repo.

At your project root enter the following commands:

> `git init` - this creates a local repo for the current project

> `git add .` - stage all files

> `git commit -m "Initial Commit"` - commit files

For the next command you will need the url of your newly created repo on Github

![alt text](/images/clone_repo.png)

> `git remote add origin {url.git}` - add remote repo called origin which points to this url

> `git push -u origin master` - pushes commit to the remote repo

# Conclusion

Version control is a great tool for any programmer to know and utilize. 

Have you every deleted a file on accident? Has your computer ever crashed and you lost all of your codebases you worked so hard on? Have you ever wanted to experiment with a new library on an existing project but wanted to do it on an isolated version of your code? 

All of these problems are solved by Git!!!

So whenever you write any code, be it enterprise, a side project, or even a demo the first thing you should do is set up your version control.

## Sources: 

> https://www.linuxjournal.com/content/git-origin-story

> http://fibrevillage.com/sysadmin/400-the-three-states-of-git

> https://buddy.works/blog/5-types-of-git-workflows

> https://kbroman.org/github_tutorial/pages/init.html

> https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf





