---
layout: default
---
# Intro to functions and JS math

## Goal

At the end of this prework, the goal is to have an understanding of what a **function** is and how to use them in JavaScript along with JavaScript built in mathematic capabilities.

## Overview

Now that you understand variables and conditionals, we will move onto a very helpful concept in JS called **functions**. A **function** is a set of instructions that can be called from other parts of the code. Imagine (unless you don't need to) you own an Amazon Echo (this is not an ad for Amazon Echo, I promise). An Echo can be used for searches, music, and more. One thing you can do with an Echo is program eletric outlets to be controlled with your voice. An example of this would be you can say "Alexa, Merry Christmas" and all of the outlets that are associated with Christmas lights are turned on. Or you can say, "Alexa, good night." and all the lights in the room shut off. This is how functions work! You create the function one time (e.g. configuring all outlets to turn off) and then you can call that function (e.g. "Alexa, good night.") every night before bed. Functions are critical to functional websites which we will be able to see below.

## Topics

### JS Math

Before we move onto functions, we first need to quickly cover math in JavaScript.

#### Concept

For the most part, it is quite intuitive:

```
var total = 3 + 4
// value of total is 7
```
Here is a table to symbols and there function:


<table>
  <thead>
    <tr>
      <th>Symbol</th>
      <th>Meaning</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>+</td><td>Addition</td></tr>
    <tr><td>-</td><td>Subtraction</td></tr>
    <tr><td>*</td><td>Multiply</td></tr>
    <tr><td>/</td><td>Divide</td></tr>
    <tr><td>**</td><td>Exponential</td></tr>
    <tr><td>===</td><td>Equal to</td></tr>
    <tr><td>></td><td>Greater than</td></tr>
    <tr><td>>=</td><td>Greater than or equal to</td></tr>
    <tr><td><</td><td>Less than</td></tr>
    <tr><td><=</td><td>Less than or equal to</td></tr>
  </tbody>
</table>

In a previous lesson, you learned about **booleans** (`true` and `false`) and how they work with **conditionals** (`if` statements). When using any comparison symbols (`>`, `<`, `>=`, `<=`), the value returned will be a **boolean**!

Let's look:

```
var result = 5 < 5.5
// value of result is `true`
```

So, a combination of JS math, **booleans**, and **conditionals** could look like:

```
var age = 10
var sentence

if (age < 8) {
  sentence = "You are a young human."
} 
else if (age > 14) {
  sentence = "You are probably in high school or much older."
}
else {
  sentence = "You are not a baby but you are not very old."
}

// value of sentence is "You are not a baby but you are not very old."
```


### Functions

#### Concept

Earlier, we said that many things can be the value of a variable. We saw that numbers (`var num = 5`) and strings (`var str = "wow"`) can be the value of variables. On top of those, **functions** can also be the value of variables. Let's look at an example:

```
var addTwoNumbers = (num1, num2) => {
  var sum = num1 + num2
  return sum
}

var total = addTwoNumbers(1, 2)

// value of total is 3
```

So, that's a lot to take it and figure out. If the code above were an English sentence, the first 4 lines would read like this: *First, I make a function called addTwoNumbers because it will add 2 numbers. I will call those numbers `num1` and `num2`. I will add those 2 numbers together and call it `sum`. Then, I will `return` the `sum` to wherever is calling this function.* 

The 6th line of code above (`var total = addTwoNumbers(1, 2)`) would read like this: *I am going to call the function `addTwoNumbers`. Since `addTwoNumbers` requires that I pass it 2 numbers, I will pass it `1` and `2`. Whatever the function returns, I will put in a variable called `total`.*

Now that we know what is generally going on, let's get into the anatomy of a function.

1. `(num1, num2)`
- The first part of any function is going to declaring your **parameters** which in this case are `num1` and `num2`. Parameters are be surrounded by parantheses and have commas in between individual parameters. You can see that we start the function with `(num1, num2)` and then use `num1` and `num2` in the next line by adding them together and setting that sum equal to `sum`, (e.g. `var sum = num1 + num2`). Parameters allow us to take in values into our function and use them even though we don't know exactly what those values will be.

2. `=> {}`
- After the parameters, we use the arrow, `=>`, to indicate we are starting the part of the function that will use the **parameters** to do something. All of this code that does stuff with the **parameters** should go between curly brackets, `{}`.

3. Function body
- In between those curly brackets are 2 lines of code, `var sum = num1 + num2` and `return sum`. The first line is pretty simple, it is simply declaring a variable `sum` and then setting it equal to the addtion of `num1` and `num2`. The next line however, isn't so clear. `return` is a keyword in JavaScript (and several other languages) that allows functions to not only do things (e.g. add 2 numbers together) but to also return values to wherever the function is being called. Without the line `return sum`, the function would add 2 numbers together, put that value in the variable `sum`, and that would be it. We couldn't use the value of `sum` outside of the function. `return` allows us to get values out of a function after the work of the function is done.

In the 6th line of code, `var total = addTwoNumbers(1, 2)`, we are calling the function **addTwoNumbers**. Since **addTwoNumbers** has two parameters, `num1` and `num2`, we have to pass 2 values. We could have passed any 2 numbers but we went with `1` and `2`. Since we passed `1` and `2` in that order, in the function **addTwoNumbers**, `num1` is equal to `1` and `num2` is equal to `2`. If we had instead called `addTwoNumbers(2, 1)`, `num1` would have 
equal to `2` and `num2` would have been equal to `1`. The order you put the values into your function call is the same as the order of the **parameters** in the function's defintion. In this example, because we are adding, the order doesn't matter. 

Let's look at an example where order does matter:

```
var divide = (num1, num2) => {
  var result = num1 / num2
  return result
}

var total1 = divide(4, 2)
var total2 = divide(2, 4)

// value of total1 is 2
// value of total2 is .5
```

By just switching the order of the values in the function calls, we get different answer.

We can use functions to do way more than just basic math. Check this out:

```
var makeSimpleGreeting = (name) => {
  var sentence = "Hi, I'm " + name
  return sentence
}

var greeting = makeSimpleGreeting("Joshua")

// value of greeting is ""Hi, I'm Joshua"
```

In the example above, we see the addition symbol `+` again, but this time, not for number but for strings. We can add strings together to create longer strings.

Here is an interesting example:

```
var makeGreeting = (name, age) => {
  var sentence = "Hi, my name is " + name + " and I am " + age + "years old."
  return sentence
}

var greeting = makeSimpleGreeting("Joshua", 27)

// value of greeting is "Hi, my name is Joshua and I am 27 years old."
```

In this example, we are not only adding strings to other strings but also add a number to the strings as well! Whenver we add a number to a string, the number just becomes a string. For example, `"some words" + 77` is equal to `"some words77"`.

Here's an example that uses **conditionals**:

```
var respondToAge = (age) => {
  var response

  if (age > 10) {
    response = "You are a young person."
  } else {
    response = "You are a person who is older than 10."
  }

  return response
}

var response1 = respondToAge(7)
var response2 = respondToAge(98)

// value of response1 is "You are a young person."
// value of response2 is "You are a person who is older than 10."
```

A more complex example that uses a number, a string, and a boolean:

```
var makeAppleGreeting = (numOfApples, nameOfAppleHolder, areApplesStolen) => {
  var greeting = "Hello, " + nameOfAppleHolder + ". You are holding " + numOfApples + " apples."

  if (areApplesStolen) {
    greeting = greeting + " You should put those apples back."
  }
  
  return greeting
}

var greeting1 = makeAppleGreeting(8, "Andre", false)
var greeting2 = makeAppleGreeting(3, "Karen", true)

// value of greeting1 is "Hello, Andre. You are holding 8 apples."
// value of greeting2 is "Hello, Karen. You are holding 3 apples. You should put those apples back."
```

#### Challenge

Go to this [CodePen](https://codepen.io/jorymullet/pen/ZEpBORq){: target='_blank'} and follow the instructions.

### Conclusion 
You can now make functions! This is a powerful tool for making your webpages much more functional and interesting.


![HTML&CSS MEME](https://media.giphy.com/media/l49JHLpRSLhecYEmI/giphy.gif)
