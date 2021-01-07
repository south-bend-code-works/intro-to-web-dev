---
layout: default
---

# Project Part 2: Virtual Pet

## Goal

At the end of this portion of the project, you will have completed the Virtual Pet project started in part 1. It will include 3 buttons that will increase (and decrease) your pet's stats. Your pet will "react" to it's state by changing it's image.
## Overview

Now that all of the "physical" components of your pet are in place, we now need to make the your page functional. As is, there are 3 buttons that do nothing, stats that don't change, and a static picture. We are going to use JavaScript to make this whole thing come to life. Prepare yourself. You're about to become the parent of a Virtual Pet.
## Steps

### Setup

Let's make sure we can see our project in the browser. Go to your desktop and find `virtual-pet`. Open that folder, right-click on `index.html`, and open in Chrome. If you see what we made in part 1, you're set.

Next, since we are going to add JavaScript to this page, we need a place to put it. The JS will go between `script` tags that will live just beneath your `body` tags.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>

  </script>
</html>
```

Once these are included, we are ready to start coding some JavaScript!

### Buttons

Last time, we made a button for each of the activities: eating, drinking, and exercising. Right now, if we click on any of the buttons, nothing happens. Let's change that.

Right now, the only reason we consider the `div`s with the class `activity-button` to be buttons is just because we have styled them to look like buttons. These `div`s are no different than any other `div`s for right now.

So, what makes a button different than any element on the screen? Seems like a goofy question but the reality is that a button is simply an element that, when clicked on, we expect something to happen. That's it. So, how do we make something happen when we click on our "buttons"?

Before we get into that, let's review **attributes**. **Attributes** are what we give to HTML elements to differentiate and control them. For example, when we give an element a **class**, we are giving it an **attribute**. All **attributes** go in the opening tag of an element.

So, why are we doing a refresher on **attributes**? The reason for this is because we are going to include an **attribute** in these `activity-button`s that will allow us to trigger an action when these elements are clicked. This **attribute** is `onclick`.

Let's look again at the **attribute** `class`. The way `class` works is that we include the word `class` in the opening tag and then set it equal to the classes we want it to have. Here's an example:

```
<div class="some-class another-class">

</div>
```

Similary, `onclick` will be in the opening tag and be set equal to something. However, instead of being set equal to a class name, it will instead of set equal to a function. An example is below.

```
<div onclick="someFunction()">

</div>
```

So let's add a simple function to all of our buttons. Let's add `onclick="console.log('Hello!')"` as an attribute to all of our functions.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
    <div class="main">
      ...
      <div class="interactive-area">

        <div class="activity-row">
          <img class="activity-icon" src="food.png" />
          <div class="activity-stat">100</div>
          <div class="activity-button" onclick="console.log('Hello!')">Eat fish</div>
        </div>
        <div class="activity-row">
          <img class="activity-icon" src="water.png" />
          <div class="activity-stat">50</div>
          <div class="activity-button" onclick="console.log('Hello!')">Drink water</div>
        </div>
        <div class="activity-row">
          <img class="activity-icon" src="exercise.png" />
          <div class="activity-stat">5</div>
          <div class="activity-button" onclick="console.log('Hello!')">Exercise</div>
        </div>

      </div>
    </div>
  </body>
  <script>
    ...
  </script>
</html>
```

If you refresh your page and click a button, you might not notice anything. That's because the function `console.log` prints whatever text we give it to the console. The way to view your console is to go to your browser, right-click on the screen, and click **Inspect**. This will bring a sidebar to the screen which will include the console which is indicated in the image below:

![]({{ site.baseurl }}/assets/img/module1/vp-console.png)

Now, if we click one of the `interactive-button`s, it will print to the console. `console.log` is a **very** helpful tool to test and debug our code.

Our `interactive-button`s do something now! They are officially buttons. At this point, however, they aren't doing any too helpful. Let's change that.

Currently, the function inside of our `onclick` attribute is `console.log`. We can instead change that to a function we put between our `script` tags. Let's make a function called `giveFood` and make that function print `Feeding pet!` to the console. Then, in our food button, let's call `giveFood()` and see if it works.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
    <div class="main">
      ...
      <div class="interactive-area">

        <div class="activity-row">
          <img class="activity-icon" src="food.png" />
          <div class="activity-stat">100</div>
          <div class="activity-button" onclick="giveFood()">Eat fish</div>
        </div>
        ...

      </div>
    </div>
  </body>
  <script>
    
    var giveFood = () => {
      console.log('Feeding pet!')
    }

  </script>
</html>
```
Woohoo! We've made a function in JavaScript that is responding to our button! We are rolling.

So, instead of just printing `Feeding pet!` to the console, let's make our food button actually increase the food stat. In order to track our food, water, and exercise stats, we are going to need **variables** to track the numbers that represent these stats. Let's add variables `food`, `water`, and `exercise` to the top of our JavaScript and start them all out with `50`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>
    
    var food = 50
    var water = 50
    var exercise = 50
    
    
    var giveFood = () => {
      console.log('Feeding pet!')
    }

  </script>
</html>
```

Now that we have **variables** in place to track our stats, let's increase the food stat by `15` every time we click the food button.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>
    
    var food = 50
    var water = 50
    var exercise = 50
    
    
    var giveFood = () => {
      food = food + 15
    }

  </script>
</html>
```

Cool! If you want to prove that is working, in the same function after you add 15 to the food stat, print `food` to the console and see it increase!

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>
    
    var food = 50
    var water = 50
    var exercise = 50
    
    
    var giveFood = () => {
      food = food + 15
      console.log(food)
    }

  </script>
</html>
```

Seems to be working as expected!

So, since we are trying to make our virtual pet a little realistic, let's make something else happen when we feed our pet. Whenever a pet eats, it's need for water and exercise increase which means those stats should decrease. In the same function that increases the `food` stat, let's also decrease `water` and `exercise` by `5`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>
    
    var food = 50
    var water = 50
    var exercise = 50
    
    var giveFood = () => {
      food = food + 15
      water = water - 5
      exercise = exercise - 5
    }

  </script>
</html>
```

Nice! Now our pet is a little more realistic.

Next, we have to create functions for our other 2 buttons, water and exercise. Let's create 2 functions, `giveWater` and `giveExercise`. In `giveWater`, let's increase `water` by `15`, decrease `food` by `5`, and decrease `exercise` by `2`. In `giveExercise`, let's increase `exercise` by 30, decrease `water` by `15`, and decrease `food` by `10`.

Make sure to set `giveWater()` as the function to the water button and `giveExercise` to exercise button.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
    <div class="main">
      ...
      <div class="interactive-area">

        <div class="activity-row">
          ...
          <div class="activity-button" onclick="giveFood()">Eat fish</div>
        </div>
        <div class="activity-row">
          ...
          <div class="activity-button" onclick="giveWater()">Drink water</div>
        </div>
        <div class="activity-row">
          ...
          <div class="activity-button" onclick="giveExercise()">Exercise</div>
        </div>

      </div>
    </div>
  </body>
  <script>

    var food = 50
    var water = 50
    var exercise = 50
    
    var giveFood = () => {
      food = food + 15
      water = water - 5
      exercise = exercise - 5
    }

    var giveWater = () => {
      water = water + 15
      food = food - 5
      exercise = exercise - 2
    }

    var giveExercise = () => {
      exercise = exercise + 30
      water = water - 15
      food = food - 10
    }

  </script>
</html>
```

Sweet! All of our functions are in place and buttons are working. However, just because our stats are changing on the JavaScript side, we now need to reflect these changes onto our HTML. 

### Updating HTML

Now that our buttons work, let's make a function that does 2 things:

1. Updates the stats in the HTML to represent the stats we have in JavaScript.
2. Updates the image to show the state of our pet.

Let's start with updating the stats in the HTML First, we need to create and name our function. Let's name it `updateHTML`. In this function, we need to get the elements that show the stats on the screen and update their `innerHTML`. In its current state, it will be hard to get specific `activity-stat` elements. If we add `id`s to each of the `activity-stat` `div`s, we will be able to easily reference them in our JS and change their `innerHTML`. Let's add the `id`s `food-stat`, `water-stat`, and `exercise-stat` to the respective `activity-stat` `div`s.

While we are in this part of the HTML anyways, let's change the starting values of stats in the HTML to all be 50, just like in the JavaScript.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
    <div class="main">
      ...
      <div class="interactive-area">

        <div class="activity-row">
          ...
          <div id="food-stat" class="activity-stat">50</div>
          ...
        </div>
        <div class="activity-row">
          ...
          <div id="water-stat" class="activity-stat">50</div>
          ...
        </div>
        <div class="activity-row">
          ...
          <div id="exercise-stat" class="activity-stat">50</div>
          ...
        </div>

      </div>
    </div>
  </body>
  <script>
    ...
  </script>
</html>
```

Nice. Now that our `activity-stat`s have `id`s, let's start adding code to our `updateHTML` function. From an earlier lesson, we learned that `document.getElementById` allows us to reference an element in HTML so that we can make changes to that element. So, if we want to reference our food stat, we would use `document.getElementById("food-stat")`. Now that we have referenced it, we need to change its `innerHTML`. We do this by appending `.innerHTML` to our reference and then setting that equal to whatever we want. In this instance, we want to set the `innerHTML` of our food stat element to the variable **food**. Similarly, we are going to want to reference the water and exercise stat elements and set their `innerHTML` to their cooresponding variables.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>

    var food = 50
    var water = 50
    var exercise = 50
    
    var giveFood = () => {
      food = food + 15
      water = water - 5
      exercise = exercise - 5
    }

    var giveWater = () => {
      water = water + 15
      food = food - 5
      exercise = exercise - 2
    }

    var giveExercise = () => {
      exercise = exercise + 30
      water = water - 15
      food = food - 10
    }

    var updateHTML = () => {
      document.getElementById("food-stat").innerHTML = food
      document.getElementById("water-stat").innerHTML = water
      document.getElementById("exercise-stat").innerHTML = exercise
    }

  </script>
</html>
```

If we refresh our page and click the buttons, nothing is happening. This is because we are never calling the function `updateHTML`. Just making the function is not enough. We need to call this function every time we update our stats in our JS. Call the function `updateHTML` at the end of every function that updates our stats.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>

    var food = 50
    var water = 50
    var exercise = 50
    
    var giveFood = () => {
      food = food + 15
      water = water - 5
      exercise = exercise - 5

      updateHTML()
    }

    var giveWater = () => {
      water = water + 15
      food = food - 5
      exercise = exercise - 2

      updateHTML()
    }

    var giveExercise = () => {
      exercise = exercise + 30
      water = water - 15
      food = food - 10
      
      updateHTML()
    }

    var updateHTML = () => {
      document.getElementById("food-stat").innerHTML = food
      document.getElementById("water-stat").innerHTML = water
      document.getElementById("exercise-stat").innerHTML = exercise
    }

  </script>
</html>
```

Whoa! Now when I click on the buttons, the stats are changing on screen! This is great news.

Now that the stats on the screen are updating, let's also update the picture to reflect our stats.

In real life, an individuals overall state can generalized to their weakest "stat". A person might be quite hydrated and in great shape, but if they are extremely hungry, their overall state will likely reflect their need for food. So, in our `updateHTML` function, before we update our image, we need to first figure out our lowest stat.

There are several ways to figure out which of the stats is the lowest. JavaScript gives us an easy way to figure out which of a group of numbers is the lowest with the built-in function `Math.min`. This function takes as many numbers as we want to give it and then returns the number with the lowest value. Here is an example:

```
var lowestNum = Math.min(1, 6, 3, -99, .34)

// value of lowestNum is -99
```

So, let's include a **variable** `lowestStat` in our `updateHTML` function that uses `Math.min` to figure out the lowest value between `food`, `water`, and `exercise`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>
  
    ...

    var updateHTML = () => {
      document.getElementById("food-stat").innerHTML = food
      document.getElementById("water-stat").innerHTML = water
      document.getElementById("exercise-stat").innerHTML = exercise

      var lowestStat = Math.min(food, water, exercise)
    }

  </script>
</html>
```

Now that we have the `lowestStat`, let's write code that makes decisions based on that value to change the image.

Before we get into the logic portion of using `lowestStat`, let's add another variable in `updateHTML` called `imageSrc`. We will use this variable in our logic to keep track of which of the images we should use based on the value of `lowestStat`.

Next, we are going to create a **conditional block** that does the following:
1. First, we are going to check to see if `lowestStat` is less than or equal to 0. If so, we are going to set the source of our `passed-out` image to the variable `imageSrc`.
  - For me, this looks like `imageSrc = "passed-out.jpeg"`.
2. If our `lowestStat` is not less than or equal to 0, we will check if `lowestStat` is less than 25. If so, our `imageSrc` should set to our `tired` image.
3. Next, we will check if `lowestStat` is less than 75. If so, will use our `neutral` image as the `imageSrc`.
4. Next, if `lowestStat` is less than 150, we will use our `upbeat` image.
5. Lastly, if none of the other conditionals were true, we will use our `exuberant` image.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>
  
    ...

    var updateHTML = () => {
      document.getElementById("food-stat").innerHTML = food
      document.getElementById("water-stat").innerHTML = water
      document.getElementById("exercise-stat").innerHTML = exercise

      var lowestStat = Math.min(food, water, exercise)
      var imageSrc

      if (lowestStat <= 0) {
        imageSrc = 'passed-out.jpeg'
      } else if (lowestStat < 25) {
        imageSrc = 'tired.gif'
      } else if (lowestStat < 75) {
        imageSrc = 'neutral.gif'
      } else if (lowestStat < 150) {
        imageSrc = 'upbeat.gif'
      } else {
        imageSrc = 'exuberant.gif'
      }
    }

  </script>
</html>
```

At the end of this **conditional block**, we should have the respective image source stored in `imageSrc` and ready to be set as the source of the image in our HTML.

Now, we have to figure out how to reference the `img` in our HTML. Like before, we will add an `id` to the `img` called `pet-image`. `pet-image` is already the class of this element. It is okay if an `id` and a class of an element are the same.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
    <div class="main">
      <div class="image-area">
        <img id="pet-image" class="pet-image" src="neutral.gif" />
      </div>
      ...
    </div>
  </body>
  <script>
    ...
  </script>
</html>
```

Now that it has an `id`, we will use `document.getElementById` to reference the element. However, this time, we don't want to change the `innerHTML`. Instead, we want to change the `src` (which is short for **source**). We will do this by appending `.src` to our image reference and setting it equal to our variable `imageSrc`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>
  
    ...

    var updateHTML = () => {
      document.getElementById("food-stat").innerHTML = food
      document.getElementById("water-stat").innerHTML = water
      document.getElementById("exercise-stat").innerHTML = exercise

      var lowestStat = Math.min(food, water, exercise)
      var imageSrc

      if (lowestStat <= 0) {
        imageSrc = 'passed-out.jpeg'
      } else if (lowestStat < 25) {
        imageSrc = 'tired.gif'
      } else if (lowestStat < 75) {
        imageSrc = 'neutral.gif'
      } else if (lowestStat < 150) {
        imageSrc = 'upbeat.gif'
      } else {
        imageSrc = 'exuberant.gif'
      }

      document.getElementById("pet-image").src = imageSrc
    }

  </script>
</html>
```

Wow! The image changes according to the lowest stat of our pet! I just think that's pretty neat.

### Simulating time

While it is cool that the HTML is responding to what is happening in the JavaScript, there is an element of our pet that is unrealistic: no maintenance. Overtime, pets naturally become hungry, thirsty, and need exercise. So, we will now simulate this in our JavaScript.

In order to represent this concept in our code, we will naturally decrease the stats of our pet every 2 seconds. In order to make something happen at regular intervals, JS gives us a neat function called `setInterval`. `setInterval` takes in 2 arguments. The first is the function that we want to run at regular intervals. The second is the amount of time we want between intervals. Time, in this case and many other cases in JS, is in milliseconds. That means if we want 2 seconds between intervals, our second argument needs to be 2000 (2 seconds === 2000 milliseconds).

An example of this could look like:

```
var sayHello = () => {
  console.log("Hello!")
}

setInterval(sayHello, 2000)
```

The code above will print `"Hello!"` to the console every 2 seconds.

So, now that we know what `setInterval` is and how to use it, we need to create the function that will decrease the stats of our pet.

Before we create the function, let's think about how much we should decrease each stat. We need to consider what stat, if ignored, will make the pet pass out the fastest.

In general, animals need water more regularly than food and food more than exercise. Our decrease in stats should represent that. So, I will have water decrease by 8 every 2 seconds, food by 4, and exercise by 2.

Now that we have decided what will go in the function, let's create it! Let's name it `agePet` and include in it all the details from above. Don't forget to run the function `updateHTML` at the end of this function so that the changes will be reflected in our HTML immediately.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>
  
    ...

    var agePet = () => {
      water = water - 8
      food = food - 4
      exercise = exercise - 2
      updateHTML()
    }

  </script>
</html>
```

Now that the function is built, we need to run `setInterval` in our code with `agePet` and the first argument and `2000` as our second.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>
  
    ...

    var agePet = () => {
      water = water - 8
      food = food - 4
      exercise = exercise - 2
      updateHTML()
    }

    setInterval(agePet, 2000)

  </script>
</html>
```

Whoa! The stats now update on their own! That makes our pet feel a little more real (and needy).

### End game

As you may have noticed, it is kind of hard to keep the pet from being passed out. But when it does, there are no consequences. Let's add some more code so that when the pet passes out, the following occurs:

1. The buttons and stats are hidden.
2. In it's place, there should be message telling the user the pet has passed out along with a button to restart the game.

First, let's create a class in our CSS that's only job is to hide an element if it is a class of that element. Let's call it `hidden` and have its only entry be `display: none;`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      ...
      .hidden {
        display: none;
      }
    </style>
  </head>
  <body>
    ...
  </body>
  <script>
    ...
  </script>
</html>
```

This will assist us in our goal to show and hide elements.

Next, let's include a new `div` in our HTML that will hold all of our end game interaction. I will class this `div` as `end-game` and also give it the `id` `end-game` (since we want to reference it in our JS). Inside of this `div` I will include 2 more `div`s, one classed `message` which will hold our end game message and another classed `activity-button` and `restart-button`. By classing it as `acitivity-button`, it will have all the styling of the buttons we already made which saves us some work. The only content in this button should be the word `Restart` since it's job will be to restart the Virtual Pet experience.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      ...
    </style>
  </head>
  <body>
    ...
    <div class="main">
      ...
      <div class="interactive-area">

        <div class="activity-row">
          <img class="activity-icon" src="food.png" />
          <div id="food-stat" class="activity-stat">50</div>
          <div class="activity-button" onclick="giveFood()">Eat fish</div>
        </div>
        <div class="activity-row">
          <img class="activity-icon" src="water.png" />
          <div id="water-stat" class="activity-stat">50</div>
          <div class="activity-button" onclick="giveWater()">Drink water</div>
        </div>
        <div class="activity-row">
          <img class="activity-icon" src="exercise.png" />
          <div id="exercise-stat" class="activity-stat">50</div>
          <div class="activity-button" onclick="giveExercise()">Exercise</div>
        </div>

        <div id="end-game" class="end-game">
          <div class="message">
            Your pet has passed out.
          </div>
          <div class="activity-button restart-button">
            Restart
          </div>
        </div>

      </div>
    </div>
  </body>
  <script>
    ...
  </script>
</html>
```

Now, if we refresh our webpage, we see that the `end-game` `div` is beneath our buttons. We don't want those to be seen at the same time. However, since we created the `hidden` class in our CSS, we can just add the class `hidden` to our `end-game` `div` and it will not be displayed.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      ...
    </style>
  </head>
  <body>
    ...
    <div class="main">
      ...
      <div class="interactive-area">
      
        ...

        <div id="end-game" class="end-game hidden">
          <div class="message">
            Your pet has passed out.
          </div>
          <div class="activity-button restart-button">
            Restart
          </div>
        </div>

      </div>
    </div>
  </body>
  <script>
    ...
  </script>
</html>
```

Alright, so our end game content exists but is now hidden.

Now, we need to build a function that hides all the `activity-row`s and shows the `end-game`. Right now, it's hard to reference the `activity-row`s because they do not have `id`s. Let's add `id`s to all of them. Let's use `food-row`, `water-row`, and `exercise-row` as their `id`s.


<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      ...
    </style>
  </head>
  <body>
    ...
    <div class="main">
      ...
      <div class="interactive-area">

        <div id="food-row" class="activity-row">
          <img class="activity-icon" src="food.png" />
          <div id="food-stat" class="activity-stat">50</div>
          <div class="activity-button" onclick="giveFood()">Eat fish</div>
        </div>
        <div id="water-row" class="activity-row">
          <img class="activity-icon" src="water.png" />
          <div id="water-stat" class="activity-stat">50</div>
          <div class="activity-button" onclick="giveWater()">Drink water</div>
        </div>
        <div id="exercise-row" class="activity-row">
          <img class="activity-icon" src="exercise.png" />
          <div id="exercise-stat" class="activity-stat">50</div>
          <div class="activity-button" onclick="giveExercise()">Exercise</div>
        </div>

        ...

      </div>
    </div>
  </body>
  <script>
    ...
  </script>
</html>
```

Now that we have `id`s on everything we want to show and hide, let's create a function that shows and hides these elements. Let's call it `toggleInteractivity`. Inside of this function, we need to reference the 4 elements (all of the `activity-row`s and `end-game`) and then toggle the class `hidden` on these elements.

*Side note: to **toggle** a class means that if an element has a certain class, that class will be removed and if an element doesn't have a certain class, that class will be applied to that element.*

The easiest way to toggle a class on an element is to reference the element and then use `classList.toggle`. Here is an example:

```
document.getElementById("some-id").classList.toggle("class-name")
```

So, in your function `toggleInteractivity`, reference all 3 `activity-row`s and `end-game`, then use `classList.toggle` to toggle the class `hidden` on all of the references.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>
  
    ...

    var toggleInteractivity = () => {
      document.getElementById("food-row").classList.toggle("hidden")
      document.getElementById("water-row").classList.toggle("hidden")
      document.getElementById("exercise-row").classList.toggle("hidden")
      document.getElementById("end-game").classList.toggle("hidden")
    }

  </script>
</html>
```

Alright, so we have built a function to toggle what is hidden and what is seen. Now, we just have to trigger the function at the appropriate time.

We want to run the function `toggleInteractivty` when our character has passed out, or when our lowest stat is less than or equal to 0. We already have a place in our code where we are checking for that exact thing! In the first conditional in our **conditional block** in `updateHTML`, we check to see if our lowest stat is less than or equal to 0. Currently, if this true, all we are doing currently is assigning our variable `imageSrc` to our `passed-out` image source. This is also where we can run `toggleInteractivity`!

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>
  
    ...

    var updateHTML = () => {
      document.getElementById("food-stat").innerHTML = food
      document.getElementById("water-stat").innerHTML = water
      document.getElementById("exercise-stat").innerHTML = exercise

      var lowestStat = Math.min(food, water, exercise)
      var imageSrc

      if (lowestStat <= 0) {
        imageSrc = 'passed-out.jpeg'
        toggleInteractivity()
      } else if (lowestStat < 25) {
        imageSrc = 'tired.gif'
      } else if (lowestStat < 75) {
        imageSrc = 'neutral.gif'
      } else if (lowestStat < 150) {
        imageSrc = 'upbeat.gif'
      } else {
        imageSrc = 'exuberant.gif'
      }

      document.getElementById("pet-image").src = imageSrc
    }

    ...

  </script>
</html>
```

If we go back to our webpage and purposely have our pet pass out, something strange happens. The `interactive-area` seems to toggle every 2 seconds between the buttons and the end game. What is happening?

Remember our `setInterval`? Well, that is still running. The function we gave to it, `agePet`, decreases all of the stats AND runs `updateHTML`. When `updateHTML` runs, it finds the `lowestStat` and then goes into the **conditional block**. If our pet is already passed out, then `lowestStat <= 0` is going to be true. This means that `toggleInteractivity` is going to be run again and again, continually toggling the `interactive-area`.

We know that the game should be over and that the toggling should stop, but the code doesn't. Let's figure out how to let it know.

Let's start by adding a variable near the top of our JS called `hasNotPassedOut` and set it equal to `true`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>

    var hasNotPassedOut = true

    var food = 50
    var water = 50
    var exercise = 50

    ...

  </script>
</html>
```

Now, we only want to toggle the `interactive-area` the first time that our lowest stat is <= 0. So, we can add another conditional within the first conditional of our **conditional block** that ensures we do not run `toggleInteractivity` again.

First, this new conditional should check if `hasNotPassedOut` is true. If it is, it should run `toggleInteractivity` and then set `hasNotPassedOut` to `false`. This ensures that when `updateHTML` is run again, it will not trigger `toggleInteractivity` more than once.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>

    ...

    var updateHTML = () => {
      document.getElementById("food-stat").innerHTML = food
      document.getElementById("water-stat").innerHTML = water
      document.getElementById("exercise-stat").innerHTML = exercise

      var lowestStat = Math.min(food, water, exercise)
      var imageSrc

      if (lowestStat <= 0) {
        imageSrc = 'passed-out.jpeg'
        if (hasNotPassedOut) {
          toggleInteractivity()
          hasNotPassedOut = false
        }
      } else if (lowestStat < 25) {
        imageSrc = 'tired.gif'
      } else if (lowestStat < 75) {
        imageSrc = 'neutral.gif'
      } else if (lowestStat < 150) {
        imageSrc = 'upbeat.gif'
      } else {
        imageSrc = 'exuberant.gif'
      }

      document.getElementById("pet-image").src = imageSrc
    }

    ...

  </script>
</html>
```

Now when my pet passes out, the end game screen stays! Whoot whoot!

However, my restart button doesn't work. Let's change that.

Just like before when trying to make our buttons work, we will need to add the attribute `onclick` to our restart button. Let's set it equal to a function we are about to make called `restart`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      ...
    </style>
  </head>
  <body>
    ...
    <div class="main">
      ...
      <div class="interactive-area">

        ...

        <div id="end-game" class="end-game hidden">
          <div class="message">
            Your pet has passed out.
          </div>
          <div class="activity-button restart-button" onclick="restart()">
            Restart
          </div>
        </div>

      </div>
    </div>
  </body>
  <script>
    ...
  </script>
</html>
```

Then, in your JS, let's create the function `restart`. This function needs to do that following:
1. Reset all of the stats back to 50.
2. Set `hasNotPassedOut` back to `true`.
3. Run `toggleInteractivity`.
4. Run `updateHTML` so that resetted stats immediately appear.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>

    ...

    var restart = () => {
      food = 50
      water = 50
      exercise = 50
      hasNotPassedOut = true
      toggleInteractivity()
      updateHTML()
    }

  </script>
</html>
```

Wow! We did it! We are back where we started so that we can trying keeping our pet alive again. Good work.

Here is the entirety of my code:

```
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        font-family: 'Courier New', Courier, monospace;
        font-weight: bold;
      }
      .header {
        padding: 32px;
      }
      .pet-name {
        font-size: 32px;
      }
      .main {
        display: grid; /* this tells `main` to be a grid*/
         /* the next line tells `main` that, since it is a grid now, to separate into 2 equal columns*/
        grid-template-columns: 1fr 1fr;
      }
      .image-area {
        background-color: #FFC292;
        display: grid;
        justify-items: center;
      }
      .pet-image {
        height: 500px;
        max-width: 100%;
        padding: 32px;
      }
      .interactive-area {
        background-color: #00BEBD;
        display: grid;
        align-items: center; /* This centers all elements inside of this element vertically */
        justify-items: center; /* This centers all elements inside of this element horizontally */
      }
      .activity-row {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr; /* This creates 3 columns of equal length */
        width: 90%; /* Makes this element almost as wide as the parent element */
        padding: 0 1rem;
        align-items: center;
      }
      .activity-icon {
        height: 40px;
        height: 40px;
      }
      .activity-button {
        background-color: #B27499;
        border-radius: 8px;
        box-shadow: 0 0 5px 0 grey;
        color: white;
        cursor: pointer;
        height: 100%;
        display: grid;
        justify-items: center;
        align-items: center;
      }
      .hidden {
        display: none;
      }
    </style>
  </head>
  <body>
    <div class="header">
      <div class="pet-name">Big L</div>
      <div class="description">He is big and not good at things.</div>
    </div>
    <div class="main">
      <div class="image-area">
        <img id="pet-image" class="pet-image" src="neutral.gif" />
      </div>
      <div class="interactive-area">

        <div id="food-row" class="activity-row">
          <img class="activity-icon" src="food.png" />
          <div id="food-stat" class="activity-stat">50</div>
          <div class="activity-button" onclick="giveFood()">Eat fish</div>
        </div>
        <div id="water-row" class="activity-row">
          <img class="activity-icon" src="water.png" />
          <div id="water-stat" class="activity-stat">50</div>
          <div class="activity-button" onclick="giveWater()">Drink water</div>
        </div>
        <div id="exercise-row" class="activity-row">
          <img class="activity-icon" src="exercise.png" />
          <div id="exercise-stat" class="activity-stat">50</div>
          <div class="activity-button" onclick="giveExercise()">Exercise</div>
        </div>

        <div id="end-game" class="end-game hidden">
          <div class="message">
            Your pet has passed out.
          </div>
          <div class="activity-button restart-button" onclick="restart()">
            Restart
          </div>
        </div>

      </div>
    </div>
  </body>
  <script>

    var hasNotPassedOut = true

    var food = 50
    var water = 50
    var exercise = 50
    
    var giveFood = () => {
      food = food + 15
      water = water - 5
      exercise = exercise - 5

      updateHTML()
    }

    var giveWater = () => {
      water = water + 15
      food = food - 5
      exercise = exercise - 2

      updateHTML()
    }

    var giveExercise = () => {
      exercise = exercise + 30
      water = water - 15
      food = food - 10

      updateHTML()
    }

    var updateHTML = () => {
      document.getElementById("food-stat").innerHTML = food
      document.getElementById("water-stat").innerHTML = water
      document.getElementById("exercise-stat").innerHTML = exercise

      var lowestStat = Math.min(food, water, exercise)
      var imageSrc

      if (lowestStat <= 0) {
        imageSrc = 'passed-out.jpeg'
        if (hasNotPassedOut) {
          toggleInteractivity()
          hasNotPassedOut = false
        }
      } else if (lowestStat < 25) {
        imageSrc = 'tired.gif'
      } else if (lowestStat < 75) {
        imageSrc = 'neutral.gif'
      } else if (lowestStat < 150) {
        imageSrc = 'upbeat.gif'
      } else {
        imageSrc = 'exuberant.gif'
      }

      document.getElementById("pet-image").src = imageSrc
    }

    var agePet = () => {
      water = water - 8
      food = food - 4
      exercise = exercise - 2
      updateHTML()
    }

    setInterval(agePet, 2000)

    var toggleInteractivity = () => {
      document.getElementById("food-row").classList.toggle("hidden")
      document.getElementById("water-row").classList.toggle("hidden")
      document.getElementById("exercise-row").classList.toggle("hidden")
      document.getElementById("end-game").classList.toggle("hidden")
    }

    var restart = () => {
      food = 50
      water = 50
      exercise = 50
      hasNotPassedOut = true
      toggleInteractivity()
      updateHTML()
    }

  </script>
</html>
```

## Conclusion

You made your own Virtual Pet! While this example might seem goofy, the skills and concepts you learned here will certainly be used on any site you may end up building. Not only that, you've made yourself a buddy in the process.

![Your Buddy]({{ site.baseurl }}/assets/img/module1/dogs_hugging.gif)

## Challenges

1. The `end-game` `div` might look a little strange since we never took time to style it well. Try and make it look good with additional CSS.
2. Whenever you close the page and reopen it, all of your stats from the previous time have been reset. Look into [cookies](https://www.w3schools.com/js/js_cookies.asp) to store your stats when you close out of the page. Then, when your page launches, check for any stored cookies and use those values to set the values of your stat variables.
