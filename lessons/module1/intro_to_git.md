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

Throughout this course we will use git and GitHub in the following ways:
- Use git to track changes to all of your code for our class assignments.
- Use git & github.com to collaborate on group projects with your classmates.
- Share a portfolio of completed projects on your public github.com profile.

## What Problem does git solve?

Say you and a friend are working on an essay together, and you decide to email updated copies of the essay back and forth as you make changes.

You write a first draft, and send it over.
Your friend makes some edits, and sends it back.

All is good, right?

Well what if then, you both make changes at the same time, and send each other your separately updated copies at the same time? How do you resolve the cases where you updated certain paragraphs differently? How can you see exactly what changes each of you made?

That's the core problem Git solves: Keeping a clear history of changes to a coding project in a way that allows multiple people to touch the code simultaneously.

## Overview

**git** is version control system that is used by the majority of professional developers.  Git tracks changes to your code so that it's easy to identify what code has changed from one version to another.

Below is a screenshot comparing two versions of the same webpage. With git can easily see what code was changed between your previous and working version of the code!
![comparing two versions of the same page](/imgs/module1/git_compare.png)

**GitHub.com** is a website that can host your git project repositories on the web, making it easy to collaborate with other developers.  

Recall that git is a *distributed* version control system. It's distributed because every developer working on a project has a complete copy of the project and all changes on their local computer (known as the project repository). All of these developers periodically sync their work and changes to this centralized, remote repository, hosted on github.com.  

![Distributed Version Control](/imgs/module1/git_distributed.png)

## Resources

Use these resources to introduce yourself to the topics and to complete the exercises:

## Git Crash Course

The following video will walk you through the basics of git and GitHub. his video closely mirrors your pre-work exercise below.

[![Git Crash course For Beginners]({{ site.baseurl }}/assets/img/module1/git_thumbnail.jpg)](ttps://www.youtube.com/watch?v=USjZcfj8yxE)

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
* [Collaborating with other developers using GitHub]()


## Installation

### Install Git
Download and Install the correct version of git for your operating system.

MAC | WINDOWS
|---|---|
[Download MAC Installer](https://sourceforge.net/projects/git-osx-installer/files/) | [Download Windows Installer](https://gitforwindows.org/)

## Creating your github.com Account
[Create your github.com account](https://github.com/join?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home)

### Important!!! Once you have created your GitHub account, please submit your username via this form: 

https://docs.google.com/forms/d/16n1_cxuQvdwyV07Zmb5Rar-0la5wZA3pAAXL5nqOadE/edit

## Exercises

Complete the following exercise to practice your new found git skills. Use the hints to reference the corresponding resources.

### Create your first git project repository

1. From the command line, create a new project repository
2. Add a file to your project repository called "index.html"
3. Add the following code to your "index.html" file
4. Stage your index.html
5. Commit your index.html

### Open the terminal or command prompt and create a new directory, my-repo, and initialize it with git-specific functions

```bash
mkdir my-repo
git init my-repo
```

### Change into the `my-repo` directory

```bash
cd my-repo
```

### Create the first file in the project

Open the project directory with visual studio code and create a new file called *index.html*

```bash
touch index.html
code index.html 
```

### Tell Git to upload your index.html file in the next change

```bash
git add index.html
```

### Give a description of what changed

```bash
git commit -m "add index.html to initial commit"
```

### Upload your changes to GitHub

Go to [github.com](https://github.com) and login to your account.  Click the plus sign in the upper right corner, and then click "New Repository"
Add a name, leave the rest of the options as defaults, and click "Create Repository".

After creating your repository, GitHub will display directions for uploading some code, but you are also welcome to follow the directions here:

```bash
git remote add origin https://github.com/<YOUR-USERNAME>/<YOUR-REPO-NAME>.git
git push origin main
```

This connects your local files to the files on github.com. If you refresh the repository page on GitHub, you should see your files

### Conclusion 

Congratulations, you now have a GitHub account with a live project! Not only is this a great way to keep track of your changes as you go, but it is also a wonderful tool to put on your resume to show-off what you've made.

![the sad truth]({{ site.baseurl }}/assets/img/module1/git_xkcd.png)
