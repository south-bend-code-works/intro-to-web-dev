---
layout: default
---

# Introduction to JavaScript (JS): Variables and Conditionals

## Goal
By the end of this lesson, you should have an understanding of JavaScript variables, conditionals, and how to use them.

## Overview
Earlier, we used an analogy of a house to describe the purposes of HTML and CSS. HTML is structure (walls, roof, foundation) and CSS is design (layout, decoration). But, if we are building a house, how do we get the functionality (electricity, plumbing, etc.)? The answer is JavaScript (JS). JS allows us to store data in databases, get data from other sites, change what's in the HTML and CSS, and much more. While just HTML and CSS may be fine for a website that simply exists to show information such as contact information or hours of business, anything more interesting than this will require JS.

## Topics

### Syntax
TODO

### Variables
One of the fundamental concepts in JS (and many other coding languages) is **variables**. Think of a **variable** as a box that we can put a value in so we can use that value or change it later. 

#### Concept
A variable requires 2 things, a name and a value. Look at the code below:

`var box = 5`

In the example above, we see 4 things; `var`, `box`, `=`, and `5`. Let's break each of these down.

1. The line starts with `var` because we are **declaring** a variable. **Declaring** a variable simply means we are creating a new variable for future use. You must **declare** a variable before you use it. For example, `box = 5`, (while allowed) is an improper way of declaring a variable. You only need to **declare** a variable one time. So, later in code, if you change the value of the variable, you do not need to use `var`.

2. The next part of code is `box` which is what we are **naming** the variable. By **naming** the variable, we can reference it later by simply typing `box` in the code. The variable can be anything you want but, if you can, make it something that reminds you of what the value means.

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

While the terms **boolean** and **conditional** may seem unfamiliar and complex, **booleans** are fairly simple and we use **conditionals** everyday! 

#### Concept

##### Booleans
A **boolean** can be one of two things, `true` or `false`. That's it. In code, we can assign **boolean** values to variables like this:
`var example = true`

Now, if we use the variable `example` later in the code, we now that it will be equal to `true`. This doesn't have use by itself, but when we add in **conditionals** booleans become a lot more powerful as a concept.

##### Conditionals
An example of a **conditional** we may see outside of coding is the following sentence: *If it snows tonight, then I will shovel my steps.* A conditional is simply *if* something is *true*, *then* something happens. Let's look at an example:

```
var activity = "I will do nothing."
var itHasSnowed = true

if ( itHasSnowed ) {
  activity = "I will shovel my steps."
}
```

In the code above, we see 2 variables, **activity** and **isHasSnowed**. We can see that, initially, the variable **acitivty** is set to `"I will do nothing."`. Later in the code, we can see that *activity* is being set again but this time to `"I will shovel my steps."`. However, setting **activity** the second time seems to surrounded by some code. Let's break this code down.

The following code (which is a snippet of the code above) is a **conditional**:

```
if ( itHasSnowed ) {
  activity = "I will shovel my steps."
}
```

A conditional can be broken down into 3 parts; `if`, `( itHasSnowed )` `{ activity = "I will shovel my steps." }`. Let's look at each part:

1. `if` is the way to **declare** a conditional. Just like with **variables** earlier, **declaring** a conditional is simply how you tell the code you are starting a **conditional**.
2. Always following the `if` in a **conditional** will be something surrounded by a `(` and a `)`. In this case, the thing surrounded by `()` is `itHasSnowed`. Whenever the thing that is surrounded by the paranthesis is `true`, the last part of the conditional will be ran. If whatever the thing that is surrounded by the paranthesis is `false` the last part of the conditional will be ignored.
3. The last part of the conditional, `{ activity = "I will shovel my steps." }`, is what will be ran if the previous part is `true`. Since the previous part, `itHasSnowed`, is `true`, `{ activity = "I will shovel my steps." }` will be ran and **activity** will be set to `"I will shovel my steps."` All the code that you want to be ran if something is true should be surrounded by a `{` and a `}` (aka curly brackets).

Whew. Maybe that makes sense on your first time through or maybe you need to read it a few more times. Either way, **conditionals** are an extremely important concept for making our code and websites do anything interesting. If you want to play with the code above, [here is a link where you can change the value of the variable **itHasSnowed** and see the outcome.](https://codepen.io/jorymullet/pen/NWRrmoK){: target='_blank'}

##### `else if` and `&&`

Let's look at a more complex example:

```
var activity = "I will do nothing."
var itHasSnowed = true
var outOfMilk = false

if ( itHasSnowed && outOfMilk ) {
  activity = "I will shovel my steps and go get milk."
} 
else if ( itHasSnowed ) {
  activity = "I will shovel my steps."
}
else if ( outOfMilk ) {
  activity = "I will go get milk."
}

// expected value of activity: "I will shovel my steps."
```

Looking at the code above, this time, there are 3 variables, **activity**, **itHasSnowed**, and **outOfMilk**. Then there is the `if` statement from before, except this time, it has 2 variables in it, both **itHasSnowed** and **outOfMilk** with a `&&` between them. This `&&` is the equivalent to the word `and`. So, if we were to read `if ( itHasSnowed && outOfMilk )` in English, we would read it as *If it has snowed and I am out of milk, then...*. Basically, both **itHasSnowed** and **outOfMilk** have to be `true` for the whole statement to be `true` and for the code `{ activity = "I will shovel my steps and go get milk." }` to be ran.

Then, underneath that statement, we see something new, `else if` statements. `else if` statements are part of the original `if` statement at the top of the **conditional block** (which is a series of **conditionals** that are grouped together and rely on each other) and are only evaluated if no other statement in the **conditional block** above them is `true`. So, in the example above, while **itHasSnowed** is `true`, **outOfMilk** is `false`, so the statement `itHasSnowed && outOfMilk` evaluates to `false`. Since the first statement is `false`, we move to the second statement which is `else if ( itHasSnowed )`. As we just said, **itHasSnowed** is `true` so code that follows it, `{ activity = "I will shovel my steps." }`, will be ran.

Since statement second coditional statement `else if ( itHasSnowed )` was `true`, the last statement, `else if ( outOfMilk )`, will be entirely ignored.

The concept of using `if` and `else if` conditionals is called **conditional chaining**. The chain will go on as long as the next **conditional** starts with `else if`. However, anytime a conditional starts with just `if`, the previous **conditional chain** is stopped and a new one is started.

Let's check out the following example:

```
var activity = "I will do nothing."
var itHasSnowed = true
var outOfMilk = true

if ( itHasSnowed && outOfMilk ) {
  activity = "I will shovel my steps and go get milk."
} 
else if ( itHasSnowed ) {
  activity = "I will shovel my steps."
}

if ( outOfMilk ) {
  activity = "I will go get milk."
}

// expected value of activity: "I will go get milk."
```

You'll see above that **itHasSnowed** and **outOfMilk** are now both `true` which means the statement `( itHasSnowed && outOfMilk )` evaluates to `true`. Since this first statement is `true`, the code `{ activity = "I will shovel my steps and go get milk." }` will be ran. So, at this point, **activity** is equal to `"I will shovel my steps and go get milk."`.

Beneath the first statement is an `else if` statement. Since it is part of the same **conditional block** as the previous `if` statement and that `if` statement evaluated to `true`, the `else if` statement will be entirely ignored.

However, beneath the `else if` statement is another `if` statement. Since the statement is an `if` instead of an `else if`, it is not part of the **conditinoal block** above it. Therefore, this `if` statement will NOT be ignored. Since it is not ignored and **outOfMilk** is true, the code `activity = "I will go get milk."` will be ran. Therefore, at the end of this code running, **activity** will be equal to `"I will go get milk."`.

##### `else` and `||`

Let's check out one last example:

```
var activity = "I will do nothing."
var itHasSnowed = false
var outOfMilk = false

if ( itHasSnowed || outOfMilk ) {
  activity = "I will shovel my steps or go get milk."
} 
else if ( itHasSnowed ) {
  activity = "I will shovel my steps."
}
else {
  activity = "I will find something productive to do."
}

// expected value of activity: "I will find something productive to do."
```

This time, we can see that both **itHasSnowed** and **outOfMilk** are `false`. We can also see that instead of `&&` being in between them, it is instead `||`. This `||` is the equivalent to the word `or`. This means that only one of **itHasSnowed** OR **outOfMilk** has to be `true` for `itHasSnowed || outOfMilk` to be considered `true`. However, since both are `false`, the whole statement evaluates to `false` and we move onto the next **conditional**. The next **conditional** is simply `else if ( itHasSnowed )` which we know is `false`.

This brings us to our last conditional, which is `else`. `else` is used at the end of a **conditional block** and is evaluated if none of the previous **conditionals** in the same **conditional block** evaluated to `true`. So, in this example, both of the **conditionals** before this `else` statement were `false`. This means that the code following the `else` statement will be ran. Since that code will be ran, the variable **activity** will be equal to `"I will find something productive to do."`.

#### Challenge

Here is a [CopePen](https://codepen.io/jorymullet/pen/poEbBBy) to play around with. 

Tasks:
- change the values of **itHasSnowed** and **outOfMilk**
- change `&&` to `||` and vice versa
- change the order or conditionals
- change where **conditional blocks** start and stop
- remove a conditional and add a conditional

Just try to get familiar with how to make **conditionals** work and how to leverage them to create desired outcomes.

## Conclusion

Wow. That's a lot to get through but so incredibly critical to making code work for you. Please spend as much time as you need familiarizing yourself with how these things work. If somethings still feel hazy or you don't totally understand what is going on, that is perfectly understandable. Just try to gain a general sense of what you are looking at and why things happen in the code.

![Keep Powering Through]({{ site.baseurl }}/assets/img/module1/power_through.gif){: style="width: 100%; max-width: 400px"}



