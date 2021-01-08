---
layout: default
---

# Introduction to JavaScript (JS): Loops

## Goal
By the end of this lesson, you should have an understanding of JavaScript Loops, why we use them, and how to code them.

## Overview

**Loops** are pretty heckin' neat. They make certain repetitive tasks simple, easy, and fast and make working with **arrays** a dream come true. They demonstrate how impressively computers can manage to do simple tasks millions of times with incredible speed.

We will look at 2 different ways to use loops: `for` loops and `while` loops.

### Concept **for** loops

We use **for** loops most often when there is a predetermined number of steps or elements (mostly working with arrays). Let's check out an example of when a `for` loop could be helpful.

```
var arr = [2,3,7,3,8,9]
```

Above we have an array `arr` that has 6 numbers in it. Let's say we wanted to build code that would add up all 6 numbers in the array. Using what we currently know, we would have to write something like this:

```
var arr = [2,3,7,3,8,9]
var total = arr[0] + arr[1] + arr[2] + arr[3] + arr[4] + arr[5]

// value of total is 32
```

This is fine and will give us the answer. But now imagine if instead of 6 numbers, it was 100 or a 1000. The code would be wildly long and incredibly unhelpful.

Luckily, loops are here to save the day. Let's look at an example of a loop:

```
var arr = [2,3,7,3,8,9]
var total = 0

var addToTotal = (num) => {
  total = total + num
}

arr.forEach(addToTotal)

// value of total is 32
```

Hmm. We recognize some of what's going on in the code above but certainly not all of it. Let's break it down line by line.

Line 1 and 2 area easy, we have from `arr` from before and are simply declaring a variable `total` and setting it equal to `0`.

Next up, we have made a function named `addToTotal`. This function takes in one argument, `num`. It takes that `num` and adds it to `total`. That's all `addToTotal` does.

Here is where things get weird, `arr.forEach(addToTotal)`. First, we see our array `arr` at the beginning. Then there is a `.` followed by `forEach` which is taking in `addToTotal` as it's argument. What is happening here?

Remember when we were talking about `.includes` before? We would code something like `arr.includes(3)` which is basically asking *Does the array `arr` include the number 3?* and then we would get be `true` or `false`. `.forEach` is similar to `.includes`, except instead of giving it the number `3` or some element to look for in the array `arr`, we are instead giving `.forEach` a function to do to every element in the array `arr`.

`.forEach` needs to be passed a function that takes in 1 argument and does something with it. That's exactly what our function `addToTotal` is doing! It takes in a number and adds it to total. `.forEach` takes our function `addToTotal` and runs it on every element in `arr`. Another way of writing what is happening in the code block above could be: 


```
var arr = [2,3,7,3,8,9]
var total = 0

var addToTotal = (num) => {
  total = total + num
}

addToTotal(arr[0])
addToTotal(arr[1])
addToTotal(arr[2])
addToTotal(arr[3])
addToTotal(arr[4])
addToTotal(arr[5])

// value of total is 32
```

`.forEach` allows us to elimate all of that repetitive code. It just goes down the line of an array and runs whatever function we give to it on every element in the array. It's beautiful.

Let's checkout another example:

```
var arr = [2,3,7,3,8,9]
var newArr = []

var addOneAndPush = (num) => {
  var numPlusOne = num + 1
  newArray.push(numPlusOne)
}

arr.forEach(addOneAndPush)

// value of newArr is [3,4,8,4,9,10]
```

Let's again break down what we are seeing. First, we have `arr` which we are very familiar with. Next, we have `newArr` which is just an empty array. Our function this time is called `addOneAndPush`. It takes in a number, adds 1 to it, and then pushes that value onto the end of `newArr`. (For a reminder on what `.push` is, go [here](#concept-adding-to-arrays))

This time, the line with `.forEach` in it doesn't look quite as scary. We know that we are to give `.forEach` a function. That function that takes in one argument and does something to it. We know that `.forEach` will do that function to every element in `arr`. Thus, `newArr` ends up being identical to `arr` except every value is one greater. Pretty cool stuff.

Let's look at one last example:

```
var arrOfPeople = [{age: 18, name: "Jack"}, {age: 29, name: "Jill"}, {age: 13, "Tim"}]

var sumOfAges = 0

var addAge = (person) => {
  sumOfAges = sumOfAges + person.age
}

arrOfPeople.forEach(addAge)

// value of sumOfAges is 60
```

This time, instead of an array of numbers, we have an array of **objects** called `arrOfPeople`. Also, we have a variable called `sumOfAges` that starts at 0.

Next we have a function, `addAge`, that takes in one argument called `person`. It then adds the `age` of that `person` to `sumOfAges`.

Lastly, we have `.forEach` appended onto `arrOfPeople` with the function `addAge`. This whole block of code written in English would read: *I have an array of people. I want to know the sum of their ages. For each person, find their age and add it to the sum of their ages.*

What a handy tool `.forEach` is ending up being!

### Challenge

Go to this [CodePen](https://codepen.io/jorymullet/pen/KKgqQYY){: target='_blank'} and follow the instructions.


### Concept: **while** loops

While **for** loops are really good for doing something to every element in an array, sometimes we need to do a task repeatedly without working with arrays.

**For** loops do something to every element in an array and then they are done. **While** loops, on the other hand, continue to *loop* until a certain condition is no longer `true`. Here is an example:

```
var total = 0
var counter = 0
var amountToAdd = 1

while (counter < 10) {
  total = total + amountToAdd
  amountToAdd = amountToAdd + 1

  counter = counter + 1
}

// value of total is 55

```

Alright, let's break down what we are looking at. First, we have 3 variable, `total`, `counter`, and `amountToAdd`. That part we are familiar with.

Then comes the word `while`, followed by `(counter < 10)`, ending with curly brackets (`{}`) with some code inside. The term `while` indicates we are about to enter a **while** loop. Everything inside the curly brackets will repeat UNTIL `counter < 10` is no longer `true`. Said in an English sentence, this is what the code would say: *I have 3 variables, total, counter and amountToAdd. Until the variable counter is no longer less than 10, do the following: add amountToAdd to total and increase both amountToAdd and counter by 1.*

Looking at the code, it would go like this:
1. We get to the **while** loop. Since `counter` is `0` and therefore less than `10`, we enter the loop.
2. `total` gets `amountToAdd` added to it so it is now worth `1`.
3. `amountToAdd` gets `1` added to it and it is now worth `2`.
4. `counter` gets `1` added to it and it is now worth `1`.
5. We go back to the top. Since `counter` is now worth `1` but still less than `10`, we go back into the loop.
...

Eventually, `counter` is worth `10` and therefore no longer less than `10`. We are then done with the **while** loop.

Pretty cool, right? We just have to create some condition that if it `true`, we repeat a task. Not so hard, right?

Let's look at another example:

```
var arr = []
var number = 1

while (arr.length <= 5) {
  arr.push(number)
  number = number * 3
}

// value of arr is [1, 3, 9, 27, 81, 243]
```

Let's also break this one down. We start with `arr` which is an empty array and `number` which is set to `1`. Then, we have a **while** loop. This loop will keep *looping* until the `length` of the array `arr` is less than or equal to `5`. Since `arr` is an empty array, its initial `length` is `0`. So we enter the loop. We `push` the value of `number` onto the array. Then, we multiply `number` by `3` before starting the loop again.

Eventually, the `length` of the array `arr` is `5` and the **while** loop stops.

That's it! Tell the **while** loop when you want it to stop and give it some logic to perform until then. Pretty neat!
### Challenge

Go to this [CodePen](https://codepen.io/jorymullet/pen/NWRgYXQ){: target='_blank'} and follow the instructions.

## Conclusion

```
counter = 0
while (counter < 3) {
  console.log("Congratulations, you have successfully completed loops!")
  counter = counter + 1
}
```

Congratulations, you have successfully completed loops!

Congratulations, you have successfully completed loops!

Congratulations, you have successfully completed loops!

<iframe src="https://giphy.com/embed/zDrQxFFgiiGoU" width="480" height="288" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/loop-infinite-surprised-patrick-zDrQxFFgiiGoU">via GIPHY</a></p>