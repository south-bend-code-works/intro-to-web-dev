---
layout: default
---

# Introduction to JavaScript (JS)

## Goal
By the end of this lesson, you should have an understanding of how to use JavaScript alongside HTML and CSS to create webpages.

## Overview
Earlier, we used an analogy of a house to describe the purposes of HTML and CSS. HTML is structure (walls, roof, foundation) and CSS is design (layout, decoration). But, if we are building a house, how do we get the functionality (electricity, plumbing, etc.)? The answer is JavaScript (JS). JS allows us to store data in databases, get data from other sites, change what's in the HTML and CSS, and much more. While just HTML and CSS may be fine for a website that simply exists to show information such as contact information or hours of business, anything more interesting than this will require JS.

## Topics

### Variables
One of the fundamental concepts in JS (and many other coding languages) is **variables**. Think of a **variable** as a box that we can put a value in and get or change later. 

#### Concept
A variable requires 2 things, a name and a value. Look at the code below:

`var box = 5`

In the example above, we see 4 things; `var`, `box`, `=`, and `5`. Let's break each of these down.

1. The line starts with `var` because we are **declaring** a variable. **Declaring** a variable simply means we are creating a new variable for future use. You must **declare** a variable before you use it. For example, `box = 5`, (while allowed) is an improper way of declaring a variable. You only need to **declare** a variable one time. So, later in code, if you change the value of the variable, you do not need to use `var`.

2. The next part of code is `box` which is what we are **naming** the variable. By **naming** the variable, we can reference it later by simply typing `box` in the code.

3. The equal symbol, `=`, is saying *the variable that is to the left of me (which is `box` in this case) is now equal to whatever is right of me (which is `5`)*. So, if we use `box` later in the code, it will be equal to `5`.

4. As we just covered, `5` is the value that is now what `box` is equal to.  This could have been many things. It could have been other numbers (`1`, `900`, `3.14159`), letters and words (which we call **strings**), and a variety of other things. 
  - In JS, the way we assign **strings** to variables is by wrapping the words or letters inside of quotes (e.g. `''`)
  - An example of this would be `var box = 'I like to code!'`.
  - Now, if we use the variable `box` later in the code, it's value will be `'I like to code!'`.
  - The following is incorrect `var box = I like to code!` because the **string** is not inside of quotes.

#### Practice

The following link will take you to a site called CodePen. It will allow you to practice concepts you learn here. When you make changes to the code, it will automatically update in the preview after a second or two.

- Challenge: Change the value of variable `number` to your favorite number.
- Challenge: Change the value of variable `number` to `'nunya business.'`
- Hints:
  - Only change code in box labeled **JS**
- [Click here for challenge](https://codepen.io/jorymullet/pen/mdrEwxM?editors=1010){: target='_blank'}

### Booleans and Conditionals

While the terms **boolean** and **conditional** may seem unfamiliar and complex, **booleans** are fairly simple and **conditionals** we use everyday! 

#### Concept

##### Booleans
A **boolean** can be one of two things, `true` or `false`. That's it. In code, we can assign **boolean** values to variables like this:
`var example = true`

Now, if we use the variable `example` later in the code, we now that it will be equal to `true`. This doesn't gain us anything right now until we look at **conditionals**.

##### Conditionals
An example of a **conditional** we may see outside of coding is the following sentence: *If it snows tonight, I will shovel my steps.*.