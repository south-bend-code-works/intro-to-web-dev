---
layout: default
---

# Introduction to JavaScript (JS): Arrays

## Goal
By the end of this lesson, you should have an understanding of JavaScript Arrays, why we use them, and how to code them.

## Overview
An array is a data structure consisting of a collection, or list, of elements.  Arrays are ordered.  Also, arrays in javascript can consist of any types of elements (e.g. strings, numbers, objects, etc).

### Concept: Making arrays
Earlier, we saw that variables could be both numbers and strings like so:

```
var aNumber = 5
var aString = 'Hi there!'
```

But there are more things in coding than just numbers and strings. One of those things is an **array**:

```
var anArray = [1,2,3]
```

What are we looking at here? Let's start with what we know. We know that `var` means we are declaring a variable and `anArray` is going to be the name of that variable. Then, we know that the `=` means we are **assigning** whatever is to the right of the `=` to the variable `anArray`. But what is `[1,2,3]`?

`[1,2,3]` is an **array**. An **array** is a list of elements. The elements in this case are numbers but they can be strings, other arrays, or anything really. You know something is an **array** if it stars with `[`, `]`, and the elements on the inside are separated by commas. The following is an example of another array:

```
var anotherArray = ['cat', 5, [13, 'dude']]
```

We can see in the **array** above, we first have the string `'cat'`, the number `5`, and finally another **array** with 2 elements in it, `13` and `'dude'`.

### Challenge

Go to this [CodePen](https://codepen.io/jorymullet/pen/qBaaBVE){: target='_blank'} and follow the instructions.

### Concept: Adding to arrays
So, we know what **arrays** look like and how to make them. But once an **array** is made, how do we add to it? And how do we get one of it elements?

Let's start with the first question, how to add to an array? Let's look at an example:

```
var arr = []
arr.push(5)

// value of arr is [5]

```

In order to add an element to an **array**, we first type the name of the **array** (in this case, `arr`) and then add `.push` after it. Then, whatever elements we want to add to the **array**, we put in paranthesis behind `arr.push`. This is telling the **array** to add whatever element we are passing into `.push` to the end of the **array**. 

Another example:

```
var arr = []

arr.push(5)
arr.push(10)
arr.push(20)

// value of arr is [5, 10, 20]
```

The above example shows us first setting `arr` equal to an empty **array**. Then we **push** 3 elements into the **array**, first the `5`, then the `10`, and lastly the `20`. Each element is being added to the back of the **array**.

### Challenge

Go to this [CodePen](https://codepen.io/jorymullet/pen/GRjjQMb){: target='_blank'} and follow the instructions.

### Concept: Getting values from an array

Okay, so we know how to make and add to an array, but how do we access individual elements inside an **array**? Chech out the code below:

```
var arr = [1,2,3,4]

var aNumber = arr[2]
var anotherNumber = arr[3]

// value of aNumber is 3
// value of anotherNumber is 4
```

Above, the first thing did was make an array, `[1,2,3,4]`. Then, in the next line, we are declaring a variable `aNumber` and assigning `arr[2]` to it. What does `arr[2]` mean?

`arr[2]` is saying this: *From of the array `arr`, get the element that is at the 2nd index.* BUT, looking at the comment in the code, it says that `aNumber` is equal to `3`. However, it looks like `3` is in the 3rd spot, not the 2nd. **In code, we do not consider the first element in an array to be at the 1st index, but at the 0th index.**{: .red} This can be very annoying when first learning to code but eventually makes a lot of sense.

So, in the code above, if we wanted to get the first value in `arr`, we would have to use `arr[0]`. Again, this may not make sense now but is actually a really nice feature of coding.

### Challenge

Go to this [CodePen](https://codepen.io/jorymullet/pen/YzGGevM){: target='_blank'} and follow the instructions.

### Concept: Additional array functionality

Now that you have the basics down, here are some other helpful things you can do with arrays

#### Length

Often, when working with arrays, knowing the length of an array will be helpful. Luckily, it's easy: 

```
var arr = [1,2,3]
var len = arr.length

// value of len is 3
```

#### Concatenation

Sometimes, we will want to combine 2 arrays into 1. The fancy, coding name for this process is called **concatenation**. JS makes this easy:

```
var arr1 = [1,2,3]
var arr2 = [3,4,5]

var longArr1 = arr1.concat(arr2)

// value of longArr1 is [1,2,3,3,4,5]

var longArr2 = arr2.concat(arr1)

// value of longArr2 is [3,4,5,1,2,3]
```
#### Includes

Occasionally, we are going to wonder if an array has a certain element in it. By using **includes**, we can find out if an element exists in an array:

```
var arr = [1,3,5,7,9]

var is5Included = arr.includes(5)
var is8Included = arr.includes(8)

// value of is5Included is `true`
// value of is8Included is `false`
```

#### indexOf

When we want to know the index of en element in an array, we we `indexOf` to find its index. If we ask for the index of an element that isn't in an array, `indexOf` returns `-1`

```
var arr = [1,3,5,7,9]

var indexOf5 = arr.indexOf(5)
var indexOf8 = arr.indexOf(8)

// value of is5Included is 2
// value of is8Included is -1
```

### Challenge

Try out these concepts at this [CodePen](https://codepen.io/jorymullet/pen/XWjgrVW){: target='_blank'}.

## Conclusion

TODO

Wow! You just learned a ton! Excellent work. Now that you know **arrays**, **objects**, and **loops**, your ability to create interesting webpages is dramatically greater! My only question now is, *who **can** stop you?* Answer:

![](https://media4.giphy.com/media/X7PCkbUm1LYO5VqbKf/giphy.gif)