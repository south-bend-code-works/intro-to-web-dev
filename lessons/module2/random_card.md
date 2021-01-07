---
layout: default
---

# Random Card Selector

## Goal

By the end of this practice problem, the goal is to create an deck of cards that we will select from randomly and disply the results on the screen.

## Overview

In the prework for this lesson, you learned both **arrays** and **objects**. We are going use our new knowledge to create a deck of cards where the  deck will be an **array** and the individual cards will be represented by **objects**. Then, we will write a function that will choose a random card from the deck and display the results on the page.

## What you will need to know

### Random in JS

Occasionally when coding, we want to create a sense of randomness. We saw this in the quidditch lesson where we randomly choose a new location for our quaffle and snitch. JavaScript a fairly easy way to create random numbers.

The built-in method used to create a random number in JS is `Math.random()`. This method will produce a number between 0 and 1. The example below is real code I ran will the actual results:

```
var ran1 = Math.random()
var ran2 = Math.random()

// value of ran1 is 0.1902916434044286
// value of ran2 is 0.027830158374312797
```
You can see from the results above, `Math.random()` returns a very specific number between 0 and 1. If I were to run the code again, I am almost guaranteed to get 2 totally different answers.

### Math.round

Let's look at the JS method `Math.round`. This is a method that takes a number and rounds it to the nearest whole number. Example:

```
var num1 = Math.round(5.4)
var num2 = Math.round(6.7)

// value of num1 is 5
// value of num2 is 7
```

Rounding is nothing new for us and JS allows us an easy way to do it. Neato!

### Combing randomness and rounding

Now, we may want a random number that isn't just between 0 and 1 but instead, maybe an integer between 0 and 100. Between `Math.random` and `Math.round`, we can make this happen!

Since `Math.random` just gives us a number between 0 and 1, we can multiply that number in order to make it larger. Then, using `Math.floor`, we can make that larger number a whole number. Below is some that will give us a random number between 0 and 100. The actual results of my code are shown:

```
var randomNum = Math.random()
var larger = randomNum * 100
var rounded = Math.round(larger)

// value of randomNum is 0.9657277725036
// value of larger is 96.57277725036
// value of rounded is 97
```

Going through the code above, we see in the first line that we are calling `Math.random` to get a random value (in this case, 0.9657277725036) and storing it in `randomNum`. Then, in the next line, we are multiplying our `randomNum` by 100 to make it larger. We could have chosen any number to multiply it by but by multiplying by 100, we are setting the maximum our number could be to 100. In the last line, we use `Math.round` to round `larger` in order to make it a whole number which, in this case, is 97.

Now that we know how to make random integers, we are ready to combine this knowledge with our previously acquired skills to create a random card selector.

## Tasks

### Create file

Before we get started coding, we need to create a folder named `random-card-selector` and save a file into it named `index.html`. Then, let's include the basic skeleton of an HTML file into `index.html`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>

  <head>
    <style>

    </style>
  </head>

  <body>

  </body>

  <script>

  </script>

</html>
```

### HTML

Okay, now that we have established the basics of our random card selector, let's add a tiny bit of HTML so that we have a place to display the random card we will eventually pick. Let's an `h1` element with the words **And our random card is:**. Under that, let's add a `h2` element that has the `id` `display` and the words **No card picked yet** between of the tags. Lastly, let's include a `button` element with the words **Pick a random card**. It should look something like this:

![]({{ site.baseurl }}/assets/img/module2/random-1.png)

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>

  ...

  <body>

    <h1>And our random card is:</h1>
    <h2 id="display">No card picked yet</h2>
    <button>Pick a random card</button>

  </body>

  ...

</html>
```

### JS

Now that we have our HTML, let's start writing some JS. Our goal is to randomly select a card from a deck where the deck is an **array**. So, let's put a variable named `deck` in our JS. `deck` should just be an empty **array**.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>

  ...

  <script>
    var deck = []
    
  </script>

</html>
```

Now that we have an **array** to put cards into, let's talk about what will make up a card. We want to represent our cards using **objects**.

Each card **object** should have 2 **keys**, a `value` and a `suit`. Let's not make the whole deck but instead, just 4 cards. I am going to create 4 variables in my code: `twoOfSpades`, `fourOfClubs`, `sevenOfDiamonds`, and `nineOfHearts`. I am going to set each variable equal to an **object** that represents the name of the variable. For example, my `twoOfSpades` will look like:

```
var twoOfSpades = {
  value: 2,
  suit: "spades",
}
```

Do this for all of the variables listed above.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>

  ...

  <script>
    var deck = []

    var twoOfSpades = {
      value: 2,
      suit: "spades",
    }

    var fourOfClubs = {
      value: 4,
      suit: "clubs",
    }

    var sevenOfDiamonds = {
      value: 7,
      suit: "diamonds",
    }

    var nineOfHearts = {
      value: 9,
      suit: "hearts",
    }
  </script>

</html>
```

Now that we have created our 4 cards, let's use `.push` to add them all to our deck.

Hint: For a reminder about how to use `.push` to add elements to an **array**, look [here](intro_to_js_arrays.html#concept-adding-to-arrays).
{: .red}


<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>

  ...

  <script>
    var deck = []

    var twoOfSpades = {
      value: 2,
      suit: "spades",
    }

    var fourOfClubs = {
      value: 4,
      suit: "clubs",
    }

    var sevenOfDiamonds = {
      value: 7,
      suit: "diamonds",
    }

    var nineOfHearts = {
      value: 9,
      suit: "hearts",
    }

    deck.push(twoOfSpades)
    deck.push(fourOfClubs)
    deck.push(sevenOfDiamonds)
    deck.push(nineOfHearts)

  </script>

</html>
```

Sweet! Now we have the 4 card **objects** we made in our array. Now, let's create a function called `selectRandomCard`. Then, let's include an `onclick` attribute in our HTML `button` that calls `selectRandomCard`.


<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>

  ...

  <body>

    <h1>And our random card is:</h1>
    <h2 id="display">No card picked yet</h2>
    <button onclick="selectRandomCard()">Pick a random card</button>

  </body>

  <script>
    
    ...

    var selectRandomCard = () => {
      
    }

  </script>

</html>
```

Nice! Now, every time we click our `button`, we will call the function `selectRandomCard`.

Now we need to include code in our `selectRandomCard` function that randomly creates a number and then uses that number to get a card out of the deck. First, let's think about what limits we want to put on our random number. We know that we only have 4 cards in our deck. We also know that when we are getting a value out of an array, the first element can be gotten using the following code:

```
var firstCard = deck[0]
```

For a reminder about how to get elements from an array, click [here](intro_to_js_arrays.html#concept-getting-values-from-an-array).
{: .red}

For arrays, the indexing starts at 0. So, since our array has 4 cards, the last card is at index 3.

Note: The last index of any **array** can be gotten by finding the length of the **array** and subtracting 1 from it.
{: .red}

So, it seems like our random number needs to be a whole number between 0 and 3. Use the [example from above](combing-randomness-and-rounding), write code inside of `selectRandomCard` that generates random whole number between 0 and 3 and stores it in a variable named `randomIndex`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>

  ...

  <script>
    
    ...

    var selectRandomCard = () => {
      var rand = Math.random()
      var larger = rand * 3
      var randomIndex = Math.round(larger)
    }

  </script>

</html>
```

You can use `console.log` at the bottom of the function to print out the random number every time you click the `button`. If this seems to printing only whole numbers between 0 and 3, you have done this correctly.

Now that we have our `randomIndex`, use it to get a card **object** out of `deck` and store it in a variable named `randomCard`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>

  ...

  <script>
    
    ...

    var selectRandomCard = () => {
      var rand = Math.random()
      var larger = rand * 3
      var randomIndex = Math.round(larger)

      var randomCard = deck[randomIndex]
    }

  </script>

</html>
```

Nice! Again, don't be afraid to use `console.log` at the bottom of this function to see the value of `randomCard`.

Now that we have chosen a `randomCard`, let's display the results in the HTML. Let's put the results inside of the `h2` element with the `id` `display`. First, we need to figure out what we want to display. To keep it simple, let's just display a string that looks something like *[value] of [suit]*.

So, let's first add a variable to `selectRandomCard` name `displayString`. Then, create a string using the values in `randomCard` that follows the format of *[value] of [suit]* and set that equal to the variable `displayString`.

Hint: For a reminder about how to get **values** from an **object**, look [here](intro_to_js_objects.html#concept-get-values-from-object).
{: .red}

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>

  ...

  <script>
    
    ...

    var selectRandomCard = () => {
      var rand = Math.random()
      var larger = rand * 3
      var randomIndex = Math.round(larger)

      var randomCard = deck[randomIndex]

      var displayString = randomCard.value + " of " + randomCard.suit
    }

  </script>

</html>
```

Coolio! We now have the content we would like to put in our element with the `id` `display`.

Like we have often done already, we are going to need to reference the element `#display` and set its `innerHTML` to `displayString`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>

  ...

  <script>
    
    ...

    var selectRandomCard = () => {
      var rand = Math.random()
      var larger = rand * 3
      var randomIndex = Math.round(larger)

      var randomCard = deck[randomIndex]

      var displayString = randomCard.value + " of " + randomCard.suit

      document.getElementById("display").innerHTML = displayString
    }

  </script>

</html>
```

If you did this successfully, you should see the details of the card that was randomly selected on the screen. How neat is that!

## Conclusion

Look at you! You just created a random card selector using **arrays**, **objects**, and random numbers. You may begin feel the possibilities of what you can make starting to expand greatly, and you should! Soon, you will learn how create an entire deck of cards without having to type the details of each card. Before you know it, you'll have earned the right to have this kind of confidence:

![](https://media4.giphy.com/media/L12g7V0J62bf2/200.gif)

## Bonus Missions

This lesson wasn't long, but there are **plenty** of obvious improvements to be made:

1. The site looks like hot garbage. Add styling to help it out.
2. Currently, in order to display the result of the randomly selected card, we just have a sentence on the screen. Add some HTML and CSS to display what looks more like a card that has the details of the randomly selected card.
3. Create more cards and add them to the deck for increased excitement.
4. **Super bonus:** Display all of the cards in the deck on the screen. Allow for the user to select which card they think will be chosen. Then, use the button to randomly select a card and then notify the user whether they were right or wrong in their guess.


