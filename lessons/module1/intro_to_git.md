---
layout: default
---

---
layout: default
---
# Intro to GIT and GITHUB

## Goal

At the end of this prework, you will be able to:
- Describe why GIT and GitHub.com are two of the most important tools for helping developers track changes to and colloborate on code.
- Use the basic and most important commands such as `git add`, `git commit`, `git status`, `git push` and more!
- Save your code to your remote repostiory on github.com.

Throught this course we will us git and github in the following ways:
- Use git to track changes to all of your code for our class assignments.
- Use git & github.com to colloborate on group projects with your classmates.
- Share a portfolio of completed projects on your public github.com profile.

## Overview

**GIT** is a distributed version control system that is used by the overwheliming majority of professional developers.  GIT tracks changes to your code so that it's easy to identify what code has changed from one version to another.

Have you ever worked on a large term paper and needed to save multipe versions? If you've ever lost important work because you accidently deleted or overwrote hours of work you understand why tracking changes to your work is so important! 

Below is a screenshot comparing two versions of the same webpage. With git can easily see what code was changed between your previous and working version of the code!
![comparing two versions of the same page](/imgs/module1/git_compare.png)

**GITHUB.COM** is a website that can host your git project repositories on the web, making it easy to colloborate with other developers.  

Imagine if we were forced to colloborate on that term paper with dozens of other students! We would need a way to safely merge everyone's contributions to our paper together while maintaining the integrity of the term paper. Github.com helps to solve this problem by enabling teams of developers track changes and colloborate using centralized project repositorys.

Recall that git is a *distributed* version controll system. It's distributed because every developer working on a project has a complete copy of the project and all changes on their local computer (known as the project repository). All of these developers periodically sync their work and changes to this centralized, remote repository, hosted on github.com.  

![Distribiuted Version Control](/imgs/module1/git_distributed.png)

## Resources
Use these resources to introduce yourself to the topics and to complete the exercises.

### GIT Crash Course

The following video will walk you through the basics of GIT and Github. his video closely mirrors your pre-work exercise below. This video is a little long and fairly dense, so you might want to get a cup of coffee while you watch it!

[![Git & GitHub Crash Course For Beginners](http://i3.ytimg.com/vi/SWYqp7iY_Tc/hqdefault.jpg)](https://www.youtube.com/watch?v=SWYqp7iY_Tc)

GIT is very robust and as such the number of commands and features may seem a little overwhelming at first, but do not worry. It is totally okay if some things are still unclear to you, just keep pressing through and these concepts will make sense as we apply them throughout the course.

#### Key Terms
* `git init`
* `git add`
* `git commit`
* `git push`
* `git status`
* `git remote`
* `git branch`
* `git clone`


#### Lessons
* [What is GITHUB?]()
* [Getting started with GITHUB]()
* [Colloborating with other developers using GITHUB]()


## Installion

### Install Git
Download and Install the correct version of git for your operating system.

MAC | WINDOWS
|---|---|
[Download MAC Installer](https://sourceforge.net/projects/git-osx-installer/files/) | [Download Windows Installer](https://gitforwindows.org/)

### Creating your Github.com Account
[Create your github.com account]()

## Exercises

Complete the following exercise to practice your new found git skills. Use the hints to reference the cooresponding resources.

### Create your first git project reposiotry

1. From the command line, create a new project repository
2. Add a file to your project repository called "index.html"
3. Add the following code to your "index.html" file
4. Stage your index.html
5. Commit your index.html

# Open the terminal or command prompt and create a new directory, my-repo, and initialize it with git-specific functions
mkdir my-repo
git init my-repo

# change into the `my-repo` directory
cd my-repo

# create the first file in the project
Open the project directory with visual studio code and create a new file called *index.html*

# git isn't aware of the file, stage it
git add index.html

# take a snapshot of the staging area
git commit -m "add index.html to initial commit"

# create a remote repository for the project on github.com
Got to github.com and login to your account.  Click the 
# provide the path for the repository you created on github

### Share your first git project reposiotry on github.com
1. ...
2. ...

git remote add origin https://github.com/YOUR-USERNAME/my-repo.git

# push changes to github
git push --set-upstream origin main

### Conclusion 
Now you understand some of the basic concepts behind GIT! Hopefully this meme makes a little more sense to you now than it did before you started. 


![GIT MEME](TODO)
