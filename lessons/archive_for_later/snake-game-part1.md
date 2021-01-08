---
layout: default
---

# Project 2: Snake Game!

## Goal

The goal for this part of the project is to build out the beginning of the game snake. The snake will not move or grow yet. We will only establish a way to track the snakes segments, remove existing segments, and add them back.

![]({{ site.baseurl }}/assets/img/module2/snake-part1-1.png)

## Overview

In the seemingly simple game of snake, there are several tricky elements to create before we have built the all familiar arcade game. We will need to learn a few more skills before diving into this portion of the project.

## Skills you will need to know

### Event listeners

If you have ever played games online, you have likely used the directional keys (up, down, left, right) to control a character or element of the game. Currently, we do not know how to trigger events and functions when these keys are pressed.

Luckily, JS has a way for us to *listen* for these key presses and react to it. In JS, we can set up a *listener* that will react every time we press any key. Below is an example of a key listener:

```
document.addEventListener("keydown", (event) => {
  console.log("You pressed a key!")
})
```

Feel free to copy and paste that in the console of your browser. Then, after clicking back into the page, any time you hit a key, in the console log, you will see `You pressed a key!`. But what is happening in that code above?

First we have `document.addEventListener`. This is saying to the whole `document` (which is our whole page) that we are adding an event listener onto it. We could be move specific and reference a specific to add the event listener to, but we want to add it to the whole page so we just use `document`.

Now, `addEventListener` is a function that takes 2 arguments. The first is the kind of event we are listening for. In our situation, we are listening for the event `"keydown"` which is simply whenever a key is pressed down. The second argument `addEventListener` takes is a function that is triggered every time the event we are listening for occurs. In the example above, our function simply prints `You pressed a key!` to the console.

Often, when we use a `keydown` event listener, we want to know exactly what key is being pressed down. But how do we do this?

In the function we give to `addEventListener` as its second argument, that function automatically is passed an argument called an `event`. Since we set up an event listener, every time that event occurs, our `function` receives the `event`.

The `event` argument is **object** that details what the event was. Let's look at another example:

```
document.addEventListener("keydown", (event) => {
  console.log(event.code)
})
```

If you code and paste that into your console, click back onto the main page, and then start pressing keys, you will see that the console is printing out the keys you are pressing! This is great since now we can make decisions based which keys are being pressed.

Let's say we want to `console.log` the phrase `"You just pressed down."` every time the down arrow is pressed. This is what our event listener would look like:

```
document.addEventListener("keydown", (event) => {
  if (event.code === "ArrowDown") {
    console.log("You just pressed down.")
  }
})
```

If you run that code in the console, you will notice we see the phrase `"You just pressed down."` every time we press down while nothing happens if we press any other key. Pretty neat, right?

### Create, add, and remove elements in JS

We know how to type in new elements into our HTML. However, because the snake will have segments that are moving, we will need to create and add new elements to represent these segments.

Let's look at the code below:

```
...
  <body>

    <div id="holder">

      <div class="a-div"></div>

    </div>

  </body>

  <script>

    var newEle = document.createELement("div")

    newEle.className = "new-guy"
    newEle.style.height = "50px"

    document.getElementById("holder").appendChild(ele)

  </script>
...
```

In the code above, we see start with some HTML which is simply a `div` with the `id` `holder` that has a `div` inside it with class `a-div`.

Things get more interesting in the JS. First, we see the variable `newEle` being assigned to `document.createELement("div")`. To make a new element in JS, we have to use `document.createElement` and then give that function the type of element we want it to create. We could have created a `p` or an `h1` element but we chose `div` because we love `div`s.

So, now we have a new `div` in our variable `newEle`. Next, we see the line `newEle.className = "new-guy"`. We can see that we are referencing our `newEle` first. Then, we use `.className` to access `newEle`'s class name. Then, we assign `"new-guy"` as our `newEle`'s class name. This means our new `div` has the class `new-guy`. 

Then, in the next line `newEle.style.height = "50px"` we see something somewhat similar. Again, we start with `newEle`. However, this time, we access the property `style`. This is how we change the CSS of element in JS. Now that we have access the `style` of our element, we use `.height` to access the `height` property of `style`. Then, we set the `height` to `"50px"`. If said in an English sentence, this line of code would read like *Set the height of the style of the new `div` to 50px*.

Now that we have created an element, added a class to it, and changed its height to 50px, we want to actually add it to the `holder`. Until we add it to the HTML, it is just an element that exists in the JS and will never be seen on the page. That's where the next line of code comes in.

`document.getElementById("holder").appendChild(ele)` is a line that, at this point, may feel pretty intuitive. First, we reference the div `holder` by using `document.getElementById("holder")`. Then, we use `.appendChild` which means *whatever element you give me, I will put at the bottom of the HTML already inside of me*. Since `holder` has the `div` `a-div` inside of it, the element we give to it (`newEle`) will included inside of `holder` after `a-div` like so:

```
<div id="holder">

  <div class="a-div"></div>
  <div class="new-guy" style="height:50px;"></div>

</div>
```

Nice! We have figured out how to create an add elements to our HTML using only JS! However, in the game of snake, in order to simulate movement, we are going to have to both add AND remove elements. So, let's look into how to do this.
{: #remove-elements}

Take the following HTML example:

```

<div id="holder">

  <div class="segment"></div>
  <div class="segment"></div>
  <div class="segment"></div>
  <div class="segment"></div>

</div>

```

In the code above, we can see 5 `div`s: 1 with `id` `holder` which holds 4 `div`s classed `segment`. Our goal is to write code that removes all 4 `segment` `div`s. JS gives us a nice way to do using `querySelectorAll` which can be see in the following code:

```
document.querySelectorAll(".segment").forEach((element) => {
  console.log(element)
})
```

Let's break down what we are seeing above. First, we have `document.querySelectorAll`. This bit means we are going to search the whole document for all of the elements that match the string we give to it as an argument. The string we gave `document.querySelectorAll` was `".segment"`. Like CSS, we use `.` to indicate a class which in this case is `segment`. So, the line `document.querySelectorAll(".segment")` is saying *get every element with the class `segment` and put it in an array*.

So, now that we have the element we are looking for in an **array**, we can use `.forEach` to iterate over each element! In the example above, we are simply printing those elements to the console one at a time. We want to actually remove these elements from the HTML. Let's look at an example that does this:

```
document.querySelectorAll(".segment").forEach((element) => {
  document.getElementById("holder").removeChild(element)
})
```

The example above is the same as the one before except instead of printing the `element` to the console, we have a different line of code, `document.getElementById("holder").removeChild(element)`. We know what `document.getElementById("holder")` does as it simply reference the `div` with the id `holder`. This is followed by `.removeChild(element)`. The function `removeChild` looks into the element it was called on (in this case, `#holder`) for an element that matches the `element` we pass to it and then removes it.

To summarize in English what the code above is doing, it would read: *Find all elements with class `segment`. Once you have a list of those elements, for each element, look inside of `#holder` and remove that element.*

### Grid column and row start

We have used `grid` many times already before to structure our pages. Grid has powerful abilities to align items how we want and make things look orderly. We will now see how we can create a grid and then, using `grid-column-start` and `grid-row-start`, we can dictate where elements inside of a grid are in the grid. 

Check out this example:

```
<!DOCTYPE html>
<html>

  <head>
    <style>

      .grid {
        display: grid;
        grid-template-columns: repeat(5, 50px);
        grid-template-rows: repeat(5, 50px);
        border: thick solid black;
        width: fit-content;
      }
      
      .segment {
        height: 50px;
        width: 50px;
        background-color: red;
        color: white;
      }

      #segment-1 {
        grid-column-start: 1;
        grid-row-start: 1;
      }

      #segment-2 {
        grid-column-start: 5;
        grid-row-start: 5;
      }

      #segment-3 {
        grid-column-start: 3;
        grid-row-start: 2;
      }

    </style>
  </head>

  <body>

    <div class="grid">

      <div class="segment" id="segment-1">1</div>
      <div class="segment" id="segment-2">2</div>
      <div class="segment" id="segment-3">3</div>

    </div>

  </body>

</html>
```

Which looks like:

![]({{ site.baseurl }}/assets/img/module2/snake-part1-2.png)

In our HTML, we can see that we have a `div` `.grid` that surrounds the 3 `.segment` `div`s which all have unique ids.

The CSS, however, is much more interesting. First, the CSS selector `.grid` turns `.grid` into a grid and then creates a 5 by 5 grid by using `grid-template-columns: repeat(5, 50px)` and `grid-template-rows: repeat(5, 50px)`. These two lines are indicating that the grid should be 5 wide and 5 tall where the height and width of the individual spaces should be 50px by 50px. Then, just so I could see the grid, I added a border. Since `div`s always want to take up as much width as possible, I added the line `width: fit-content` so that `.grid` would only be the width of the grid within it.

Then, we have the selector `.segment`. This selector is saying that every `.segment` should be red, 50px tall, and 50px wide (which fits nicely into our `.grid`'s dimensions).

After we specify what all of the `.segments` should look like, we use the `.segment`s ids to place them in the grid. The property `grid-column-start` indicates which column of the grid the element should start where `grid-row-start` indicates which row of the grid the element should start.

Look at the code and picture until the concepts in the CSS make sense.

Hint: If you want to change the `grid-column-start` or `grid-row-start` in JS, you have to write the properties differently. JS interprets the `-` symbol as subtraction, so we have to write properties that have in the following manner:
{:.red#grid-help}

```

document.getElementById("segment-1").style.gridColumnStart = 2
document.getElementById("segment-1").style.gridRowStart = 2

```

Not a hard concept but it is easy to get tripped up by this.


## Project

### HTML and CSS

Now that you have been equipped with the tools you need to complete the first part of the project, let's start building.

First, create a folder name `snake` on your desktop and create a file in it named `index.html`. Build the skeleton of every HTML file.

If you'd like to include the title of the game at the top, go for it.

Then, create a `div` grid (with the id `snake-grid`) that is 12 by 12 with spaces 30px by 30px. Feel free to put a border around it and reduce the width to `fit-content` so that you can see where your grid is at.

Now that we have a grid, let's add to it a `div` classed `segment`. Use CSS to give it a height and width of 30px. Use whatever background color you want.

If you can see your `.segment` and it looks good, you can go ahead and remove it from the HTML. We just needed it to make sure the CSS selector `.segment` looked like you wanted it to.

### JS

Now onto the JS. We need a way to track the segments of the snake. Let's use an **array** to record to coordinates. Each of the coordinates should be an **object** with 2 keys: `x` and `y`. Both `x` and `y` will have values that are numbers representing the segment's location on the grid. Create a variable `segments` that is an array with 3 coordinates that could exist in your grid in the array as placeholders.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
var segments = [
  {x: 6, y: 5},
  {x: 6, y: 6},
  {x: 6, y: 7},
]
```

Also, include a variable named `direction` and assign it the value `"up"`. This will help us keep track of which direction our snake is headed.

Next, include an event listener [(like the one mentioned and coded above)](#event-listeners). It should listen for the event `"keydown"` and in the function you pass it, include a **conditional block**. This conditional block should include 4 **conditionals** that check for the 4 directional keys. If the down arrow is pressed, change the value of `direction` to `"down"`. Do the same with left, right, and up.

Next, create a function called `onEveryTick`. Run this function every 1 second using `setInterval`. It won't do anything yet but we will eventually add other function calls to this function that will occur every 1 second.

Then, create a function called `drawSegments`. This function iterate over all coordinates in `segments` using `.forEach`. For each coordinate, you should do the following:

1. Create a `div` and assign it to a variable
2. Add the class `"segment"` to the `div` using `.className`
3. Then, using the `x` and `y` values from the coordinates, update the style of the div so that the `gridColumnStart` is equal to the coordinates' `x` value and `gridRowStart` is equal to the coordinates' `y` value.

Hint: Look [here](#create-add-and-remove-elements-in-js) and [here](#grid-help) for clues on how to do this.
{:.red}

Now, call the function `drawSegments` inside of your function `onEveryTick`. You should now see your segments on the grid. If not, try and go through the instructions slowly and figure out where it went wrong.

At this point, every second, 3 `.segment` `div`s are being added to your grid. If you use **inspect** in Chrome and look into your `grid`, you will see that many `div`s are being added to your grid. They are just stacking up on top of each other. 

What will eventually happen is that in `onEveryTick`, we are going to first remove all the `.segment`s from the HTML, update the coordinates in JS, and then use `drawSegments` to put the `.segments` back into the HTML. For now, we are going to pass on updating the `segments` array and create the function that removes the `.segment`s from the HTML.

So, create a function named `removeSegments`. This function should first use `document.querySelectorAll` to get an array of all elements with the class `segment`. Then, it should use `forEach` to iterate over all elements. With each element, it should use `removeChild` on the element `#snake-grid` to remove the element from the grid.

Hint: Look [here](#remove-elements) for a reminder of how to remove elements.
{:.red}

Now, this function `removeSegments` should be called first in the function `onEveryTick`. After doing this, if you use **inspect** again in Chrome, you should see that you are not continually adding `div`s to your grid but instead, you have only as many as 3 at a time. The `.segments` are being removed and the added again so quickly that you may not be able to see it and that is perfect.


## Conclusion

Good work! You have built the beginning of snake along with learning neat new tricks! This stuff is in no way easy so if you don't get it immediately, that is very understand. Continue to try to make it work and use the solution as a guide to help you figure out your own solution.

![](https://media.tenor.com/images/a0dc4ec3bbf820d70d6ff5f6a2f45db9/tenor.gif)

## Solution

```
<!DOCTYPE html>

<html>

  <head>
    <style>
      body {
        font-family: 'Courier New', Courier, monospace;
      }
      #snake-grid {
        display: grid;
        grid-template-columns: repeat(12, 30px);
        grid-template-rows: repeat(12, 30px);
        border: thick solid black;
        width: fit-content;
      }

      .segment {
        width: 30px;
        height: 30px;
        background-color: red;
      }
    </style>
  </head>

  <body>
    <h1>Snake</h1>
    <div class="game-area">

      <div id="snake-grid">
        
      </div>

    </div>
  </body>


  <script>

    var direction = 'up'

    var segments = [
      {x: 6, y: 5},
      {x: 6, y: 6},
      {x: 6, y: 7},
    ]

    document.addEventListener('keydown', (e) => {
      if (e.code === 'ArrowUp') {
        direction = 'up'
      } else if (e.code === 'ArrowLeft') {
        direction = 'left'
      } else if (e.code === 'ArrowRight') {
        direction = 'right'
      } else if (e.code === 'ArrowDown') {
        direction = 'down'
      }
    })
    
    var removeSegments = () => {
      document.querySelectorAll('.segment').forEach(ele => {
        document.getElementById('snake-grid').removeChild(ele)
      })
    }

    var drawSegments = () => {

      segments.forEach((segment) => {

        var ele = document.createElement('div')
        ele.className = 'segment'
        ele.style.gridColumnStart = segment.x
        ele.style.gridRowStart = segment.y

        document.getElementById('snake-grid').appendChild(ele)

      })

    }


    var onEveryTick = () => {
      removeSegments()
      drawSegments()
    }

    setInterval(onEveryTick, 1000)

  </script>

</html>
```

## Bonus Missions

1. Connect your folder `snake` to your GitHub repo.
2. Add some styling and center your game to make it feel more like an arcade.