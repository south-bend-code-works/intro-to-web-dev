---
layout: default
---

---
layout: default
---
# Intro to git and GitHub

## Goal

At the end of this prework, you will be able to:
- Describe why git and GitHub.com are two of the most important tools for helping developers track changes to and collaborate on code.
- Use the basic and most important commands such as `git add`, `git commit`, `git status`, `git push` and more!
- Save your code to your remote repository on github.com.

Throughout this course we will us git and GitHub in the following ways:
- Use git to track changes to all of your code for our class assignments.
- Use git & github.com to collaborate on group projects with your classmates.
- Share a portfolio of completed projects on your public github.com profile.

## Overview

**git** is a distributed version control system that is used by the overwhelming majority of professional developers.  Git tracks changes to your code so that it's easy to identify what code has changed from one version to another.

Have you ever worked on a large term paper and needed to save multiple versions? If you've ever lost important work because you accidentally deleted or overwrote hours of work you understand why tracking changes to your work is so important! 

Below is a screenshot comparing two versions of the same webpage. With git can easily see what code was changed between your previous and working version of the code!
![comparing two versions of the same page](/imgs/module1/git_compare.png)

**GitHub.com** is a website that can host your git project repositories on the web, making it easy to collaborate with other developers.  

Imagine if we were forced to collaborate on that term paper with dozens of other students! We would need a way to safely merge everyone's contributions to our paper together while maintaining the integrity of the term paper. GitHub.com helps to solve this problem by enabling teams of developers track changes and collaborate using centralized project repositories.

Recall that git is a *distributed* version control system. It's distributed because every developer working on a project has a complete copy of the project and all changes on their local computer (known as the project repository). All of these developers periodically sync their work and changes to this centralized, remote repository, hosted on github.com.  

![Distributed Version Control](/imgs/module1/git_distributed.png)

## Resources
Use these resources to introduce yourself to the topics and to complete the exercises.

### GIT Crash Course

The following video will walk you through the basics of git and Github. his video closely mirrors your pre-work exercise below. This video is a little long and fairly dense, so you might want to get a cup of coffee while you watch it!

[![Git & GitHub Crash Course For Beginners](http://i3.ytimg.com/vi/SWYqp7iY_Tc/hqdefault.jpg)](https://www.youtube.com/watch?v=SWYqp7iY_Tc)
<!-- Maybe switch to the shorter https://www.youtube.com/watch?v=USjZcfj8yxE -->

Git is very robust and as such the number of commands and features may seem a little overwhelming at first, but do not worry. It is totally okay if some things are still unclear to you, just keep pressing through and these concepts will make sense as we apply them throughout the course.

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
* [What is GitHub?]()
* [Getting started with GitHub]()
* [Collaborating with other developers using Github]()


## Installation

### Install Git
Download and Install the correct version of git for your operating system.

MAC | WINDOWS
|---|---|
[Download MAC Installer](https://sourceforge.net/projects/git-osx-installer/files/) | [Download Windows Installer](https://gitforwindows.org/)

### Creating your Github.com Account
[Create your github.com account](https://github.com/join?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home)

## Exercises

Complete the following exercise to practice your new found git skills. Use the hints to reference the corresponding resources.

### Create your first git project repository

1. From the command line, create a new project repository
2. Add a file to your project repository called "index.html"
3. Add the following code to your "index.html" file
4. Stage your index.html
5. Commit your index.html

# Open the terminal or command prompt and create a new directory, my-repo, and initialize it with git-specific functions

```bash
mkdir my-repo
git init my-repo
```

# Change into the `my-repo` directory

```bash
cd my-repo
```

# Create the first file in the project

Open the project directory with visual studio code and create a new file called *index.html*

```bash
code .
```

# git isn't aware of the file, stage it

```bash
git add index.html
```

# Take a snapshot of the staging area

```bash
git commit -m "add index.html to initial commit"
```

# Create a remote repository for the project on github.com

Got to github.com and login to your account.  Click the 

# Provide the path for the repository you created on github

### Share your first git project repository on github.com
1. ...
2. ...

```bash
git remote add origin https://github.com/<YOUR-USERNAME>/my-repo.git
```

# Push changes to github

```bash
git push --set-upstream origin main
```

### Conclusion 
Now you understand some of the basic concepts behind GIT! Hopefully this meme makes a little more sense to you now than it did before you started. 


![GIT MEME](TODO)
