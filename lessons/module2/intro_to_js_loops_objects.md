---
layout: default
---

# Introduction to JavaScript (JS): Objects and Loops

## Goal
By the end of this lesson, you should have an understanding of JavaScript loops, object, arrays, and how them in code.

## Overview
This lesson will build on our current knowledge of JavaScript variables and conditionals in order to do repetitive tasks quickly and use JS objects to manage data.

## Topics

### Arrays

#### Concept: Making arrays
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

#### Challenge

Go to this [CodePen](https://codepen.io/jorymullet/pen/qBaaBVE){: target='_blank'} and follow the instructions.

#### Concept: Adding to arrays
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

#### Challenge

Go to this [CodePen](https://codepen.io/jorymullet/pen/GRjjQMb){: target='_blank'} and follow the instructions.

#### Concept: Getting values from an array

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

#### Challenge

Go to this [CodePen](https://codepen.io/jorymullet/pen/YzGGevM){: target='_blank'} and follow the instructions.

#### Concept: Additional array functionality

Now that you have the basics down, here are some other helpful things you can do with arrays

##### Length

Often, when working with arrays, knowing the length of an array will be helpful. Luckily, it's easy: 

```
var arr = [1,2,3]
var len = arr.length

// value of len is 3
```

##### Concatenation

Sometimes, we will want to combine 2 arrays into 1. The fancy, coding name for this process is called **concatenation**. JS makes this easy:

```
var arr1 = [1,2,3]
var arr2 = [3,4,5]

var longArr1 = arr1.concat(arr2)

// value of longArr1 is [1,2,3,3,4,5]

var longArr2 = arr2.concat(arr1)

// value of longArr2 is [3,4,5,1,2,3]
```
##### Includes

Occasionally, we are going to wonder if an array has a certain element in it. By using **includes**, we can find out if an element exists in an array:

```
var arr = [1,3,5,7,9]

var is5Included = arr.includes(5)
var is8Included = arr.includes(8)

// value of is5Included is `true`
// value of is8Included is `false`
```

##### indexOf

When we want to know the index of en element in an array, we we `indexOf` to find its index. If we ask for the index of an element that isn't in an array, `indexOf` returns `-1`

```
var arr = [1,3,5,7,9]

var indexOf5 = arr.indexOf(5)
var indexOf8 = arr.indexOf(8)

// value of is5Included is 2
// value of is8Included is -1
```

#### Challenge

Try out these concepts at this [CodePen](https://codepen.io/jorymullet/pen/XWjgrVW){: target='_blank'}.

### Objects

#### Concept: Making objects

Now that we know strings, numbers, and arrays, the next thing to learn are **objects**.

Below is an example of an **object** being set to the variable `person`:

```
var person = {
  name: "Joshua",
  age: 27,
  occupation: "Web Developer",
}
```

So, first we can see a variable named `person`. Then we see curly brackets with words, numbers, and strings inside. What is going on? Let's break what we are seeing down bit by bit. 

To start, every object will start with a `{` and end with a `}` as you can see from the example above. So let's strip away everything else except the stuff in the middle:

```
  name: "Joshua",
  age: 27,
  occupation: "Web Developer",
```

By just looking at these 3 lines, things become clearer. It seems that variable `person` is an **object** where its `name` is `"Joshua"`, the `age` is `27`, and the `occupation` is `"Web Developer"`. In the example above, `name`, `age`, and `occupation` are all **keys** and `"Joshua"`, `27`, and `"Web Developer"` are all **values**. **Objects** are simply a list of **key**/**value** pairs separated by commas. **Keys** are always just a word that describes the **value** (which can be a number, string, an array, or even another **object**).

**Objects** are really neat because they allow us to describe and create concepts in code like how I described a `person` above. Let's look at another example:

```
var cat = {
  fur: "long",
  age: 3,
  favoriteActivities: ["pouncing", "eating", "sleeping"],
}
```

Using only code, I was able to create and describe a `cat`! This might seem silly now but **object's** practical use is endless. Let's look at one more example before moving on:

```
var playingCard = {
  suit: "hearts",
  value: 9,
}
```

In the previous example, I created a `playingCard` with just a few lines of code. I didn't even introduce the idea of a playing card nor did I have to. The **object** and variable name made it obvious. This is one reason why **objects** are so useful and powerful.

#### Challenge

Go to this [CodePen](https://codepen.io/jorymullet/pen/RwGgjMe){: target='_blank'} and follow the instructions.


#### Concept: Get values from object

Now that we know how to build **objects** in JS, it would also be useful to be able to get values we have put in our **objects**.

Let's look back at the first example: 

```
var person = {
  name: "Joshua",
  age: 27,
  occupation: "Web Developer",
}
```

Above, we have the variable `person`. Imagine later in my code, I wanted to get the `name` of `person`. It is as simple as this:

```
var justTheName = person.name

// value of justTheName is "Joshua"
```

Pretty cool, right? All we do is add a dot (`.`) and the **key** (`name`) and we will get the **value**.

Using the same **object** `person`, I can create an introduction like so:

```
var intro = "Hi! I'm " + person.name + ". I am " + person.age + " years old and work as a " + person.occupation + "."

// value of intro is "Hi! I'm Joshua. I am 27 years old and work as a Web Developer."
```

Wow! So handy.

#### Challenge

Go to this [CodePen](https://codepen.io/jorymullet/pen/LYRLOar){: target='_blank'} and follow the instructions.


#### Concept: Edit an object

We now know how to build **objects** and get **values** from them. But what if we want to add a value to an existing object? What about deleting a **key**/**value** pair? Or overwriting an existing **value**? These things are all possible and simple with **objects**.

Let's again start with our `person` **object** as the example:

```
var person = {
  name: "Joshua",
  age: 27,
  occupation: "Web Developer",
}
```

Let's first look at adding a **key**/**value** pair:

```
person.nameOfPet = "Fido"

// value of person is {
//  name: "Joshua",
//  age: 27, 
//  occupation: "Web Developer", 
//  nameOfPet: "Fido",
//}
```

As you can see from the example above, if we want to add to an **object**, we simply must reference the **object** (`person`), add a dot (`.`), name the **key** (`nameOfPet`), and set that all equal to the **value** we want (`"Fido"`). Easy peasy!

Next, let's look at an example of deleting a **key**/**value** pair from an **object**:

```
delete person.occupation

// value of person is {
//  name: "Joshua",
//  age: 27, 
//  nameOfPet: "Fido",
//}
```

It looks a little strange, but the way to delete from an **object** is to type the `delete` followed by the reference to the **object** (`person`), add a dot (`.`), followed by the name of the **key** that you are trying to delete.

Finally, let's look at overwriting a **key**/**value** pair that already exists.

```
person.name = "Ryan"

// value of person is {
//  name: "Ryan",
//  age: 27, 
//  nameOfPet: "Fido",
//}
```

We can overwrite **key**/**value** in the exact same way we add new **key**/**value** pairs. The only difference is that **key** already existed.

#### Challenge

Go to this [CodePen](https://codepen.io/jorymullet/pen/LYRLeBo){: target='_blank'} and follow the instructions.


### Loops

**Loops** are pretty heckin' neat. They make certain repetitive tasks simple, easy, and fast and make working with **arrays** a dream come true. They demonstrate how impressively computers can manage to do simple tasks millions of times with incredible speed.

We will look at 2 different ways to use loops: `for` loops and `while` loops.

#### Concept **for** loops

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

#### Challenge

Go to this [CodePen](https://codepen.io/jorymullet/pen/KKgqQYY){: target='_blank'} and follow the instructions.


#### Concept: **while** loops

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

That's it! Tell the **while** loop when you want it to stop and give it some logic to perfom until then. Pretty neat!
#### Challenge

Go to this [CodePen](https://codepen.io/jorymullet/pen/NWRgYXQ){: target='_blank'} and follow the instructions.

## Conclusion

Wow! You just learned a ton! Excellent work. Now that you know **arrays**, **objects**, and **loops**, your ability to create interesting webpages is dramatically greater! My only question now is, *who **can** stop you?* Answer:

![](https://media4.giphy.com/media/X7PCkbUm1LYO5VqbKf/giphy.gif)