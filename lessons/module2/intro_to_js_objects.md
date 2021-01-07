---
layout: default
---

# # Introduction to JavaScript (JS): Objects

## Goal
By the end of this lesson, you should have an understanding of JavaScript Objects, why we use them, and how to code them.

## Overview
An `object` is type of variable that contains an unordered set of related properties.  Each a property is an association between a name (or key) and a value.  The name (or key) is always a string, and the value can be any type of object (e.g. a number, a string, another object, or even a function!)

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

## Conclusion

TODO