---
layout: default
---

# Practice Problem: Build a deck of cards


## Goal
At the end of this practice problem, you should have created a deck of cards in javascript and displayed the cards in your console.

## Overview
A deck has 52 cards. Before, we've seen how tedious it can be to create objects that represent cards. Creating only 4 cards before was annoyingly time consuming and the likelihood of a typo is high when writing them by hand. We will figure out a way to instead write 52 into an array quickly and accurately.

### Getting started
In order to start your page, you will need a new folder and a new file. Go to your desktop and create a new folder called `deck_of_cards`. Then, open up VS Code and create a new file called `index.html` and save it inside of your `deck_of_cards` folder.

As always, you need to start will the bare bones of a website which is this:

```
<!DOCTYPE html>
<html>
  <head>
    <style>

    </style>
  </head>
  <body>
    Hello world!
  </body>
  <script>

  </script>
</html>
```

After copying and pasting that into the file, go to the folder `deck_of_cards` on you desktop, open it, right-click on `index.html`, and choose to open in your browser. Confirm that you can see `Hello world!`. If so, you are ready to get started.

### Creating a deck

 A deck has 52 cards which are made up of 4 suits with 13 values within each suit. There are several ways we could represent this deck of cards in JS. For our purposes, I believe the easiest way for us to represent the deck is to use both an **arrays** and **objects**. 

Each individual card will be an **object** with 2 **key**/**value** pairs, the **suit** (`"hearts", "diamonds"`, etc.) and the **value** (`1`, `2`,). We are going to create an **object** for each card and then put all 52 cards into an **array**. This will allow us to do things like shuffle and deal cards without much work.

So, when it comes to making the individual card objects, we can do 1 of 2 things:
1. We manually type out each card. (Nope)
2. We use 2 **for** loops to create the 52 cards quickly and easily. (Yep)

Alright, so let's create a **function** that will build us a new deck. Let's call it `buildDeck`. `buildDeck` will need to return an **array** of 52 card objects. Let's include some of the parts of the **function** we know will be in there. Create a **variable** name `newDeck` that is an empty **array** in our function `buildDeck` and let's have our **function** return `newDeck`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <script>

    var buildDeck = () => {
      var newDeck = []

      return newDeck
    }

  </script>
</html>
```

Alright, so we have a function that returns an empty **array**. Let's add some more code so that the `newDeck` isn't empty at the end of `buildDeck`.

In order to create 52 cards, we need to create a card for every suit and for every value (1-13). So, let's first make arrays representing the suits and values and put them inside of `buildDeck`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <script>

    var buildDeck = () => {
      var newDeck = []
      var suits = ['heart', 'spade', 'diamond', 'club']
      var values = [1,2,3,4,5,6,7,8,9,10,11,12,13]

      return newDeck
    }

  </script>
</html>
```

Okay, so we have **arrays** for both our values and suits. Now, how do we use loops to create the cards and add them to `newDeck`? Let's review how we wanted to make a card:

```
var card = {
  suit: 'heart',
  value: 4
}
```

The variable `card` above represents the 4 of hearts.

Now that we have confirmed what the card **object** will look like, let's start building loops.

Before we get started, let's learn another way to think about using `.forEach`. In previous examples, we saw `.forEach` used like this:

```
var total = 0
var nums = [1,2,3,4,5,6]

var addToTotal = (num) => {
  total = total + num
}

nums.forEach(addToTotal)

// value of total is 21
```

In the example above, we declare the variables `total` and `nums`. Then we create a **function** name `addToTotal`. Later, in the `.forEach`, we reference `addToTotal`. However, we don't ever have to give that **function** `addToTotal` a name. We don't have to first create it and then reference the name of the **function** later. Instead, where we typically put the name of the **function** in `.forEach`, we can instead just drop the entire **function** there instead like so:

```
var total = 0
var nums = [1,2,3,4,5,6]

nums.forEach((num) => {
  total = total + num
})

// value of total is 21
```

The results will be the exact same. The only difference is that, instead of creating a **function**, giving it a name (`addToTotal`), and then referencing it later when using `.forEach`, we can instead just drop the **function** into the `.forEach`. This might not seem that helpful right now, but this is really nice when we decide to use a **for** loop within another **for** loop.

Okay, so we have our arrays (`suits` and `values`) that we have to loop over. Let's first create a **for** loop that loops over the strings in **suits**:

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <script>

    var buildDeck = () => {
      var newDeck = []
      var suits = ['heart', 'spade', 'diamond', 'club']
      var values = [1,2,3,4,5,6,7,8,9,10,11,12,13]

      suits.forEach((suit) => {
        console.log(suit)
      })

      return newDeck
    }

  </script>
</html>
```

The previous hint code will print all of the strings in `suits` in order. Notice, we are using `.forEach` without referencing the name of a **function** but instead by dropping the **function** directly into the `.forEach`.

Okay, so we have code that loops over all of the elements in `suits` but still isn't adding any cards to `newDeck`. We also have to loop over all the elements in `values`. Maybe we could do it like this:

```
<!DOCTYPE html>
<html>
  ...
  <script>

    var buildDeck = () => {
      var newDeck = []
      var suits = ['heart', 'spade', 'diamond', 'club']
      var values = [1,2,3,4,5,6,7,8,9,10,11,12,13]

      suits.forEach((suit) => {
        console.log(suit)
      })

      values.forEach((value) => {
        console.log(value)
      })

      return newDeck
    }

  </script>
</html>
```

The issue with the code above is that we first loop over all of `suits` and then we loop over `values`. To make a card **object**, we need to have access to both `suit` and `value` at the same time.

The way to have access to the `suit` and `value` at the same time is to have a loop **within** a loop. We can do this by putting the `values` loop inside of the `suits` loop.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <script>

    var buildDeck = () => {
      var newDeck = []
      var suits = ['heart', 'spade', 'diamond', 'club']
      var values = [1,2,3,4,5,6,7,8,9,10,11,12,13]

      suits.forEach((suit) => {
        console.log(suit)
        values.forEach((value) => {
          console.log(value)
        })
      })

      return newDeck
    }

  </script>
</html>
```

The previous hint code would result in the following: First, we have a `.forEach` on `suits`, so we will loop over each of the `suits`. The first in `suits` is `"heart"`. When we start the loop, we first print the value of `suit` (which is `"heart"`) to the console. Then, we have another `.forEach`, this time on `values`. So, we then print to the console every `value` in `values`. After all of these print, we go to the top of the `suits` loop and print the next element in `suits` which is `"spade"`. Then we print every `value` in `values` and so on and so forth.

This could be a lot to take in so feel free to look at the code and read the explanation until it begins to click.

Alright, now, in our `values` loop, we will have access to both `suit` and `value`. Let's create a variable in this `values` loop called `card`. `card` should be an **object** with 2 **key**/**value** pairs. The 2 **keys** should be `suit` and `value` and the 2 **values** should be `suit` and `value`, respectively. Then, we should `push` `card` onto `newDeck`, like so:

```
<!DOCTYPE html>
<html>
  ...
  <script>

    var buildDeck = () => {
      var newDeck = []
      var suits = ['heart', 'spade', 'diamond', 'club']
      var values = [1,2,3,4,5,6,7,8,9,10,11,12,13]

      suits.forEach((suit) => {
        values.forEach((value) => {

          var card = {
            suit: suit,
            value: value,
          }

          newDeck.push(card)

        })
      })

      return newDeck
    }

  </script>
</html>
```

If you understand the **loop** within a **loop** that's great. However the variable **card** might still be a little confusing. We are used to seeing **objects** being made in the following manner: 

```
var card = {
  suit: "heart",
  value: 4
}
```

Directly above, the **values** are either a string or a number. However, in the code with the double loops, the card object instead looks like this:

```
var card = {
  suit: suit,
  value: value,
}
```

It may looks strange since the words `suit` and `value` are being repeated but the same thing is going on in both of the previous examples. The only difference is that, in the second one, the second instances of `suit` and `value` are parameters that represent whatever element the loops are on. Take some time on this until it makes sense.

Cool! Now that we have created a **loop** within a **loop**, used those loops to create card **objects**, and then `push`ed those card **objects** onto an **array**, we have a function that returns a full deck! This is a great start to creating any card game. Copy and paste the following code to see the deck printed in the console:

```
<!DOCTYPE html>
<html>
  ...
  <script>

    var buildDeck = () => {
      var newDeck = []
      var suits = ['heart', 'spade', 'diamond', 'club']
      var values = [1,2,3,4,5,6,7,8,9,10,11,12,13]

      suits.forEach((suit) => {
        values.forEach((value) => {

          var card = {
            suit: suit,
            value: value,
          }

          newDeck.push(card)

        })
      })

      return newDeck
    }

    var deck = buildDeck()
    console.log(deck)

  </script>
</html>
```

## Conclusion

Wow. Loops within loops! What a wild time to be alive but what a delightful thing to know! Now, we can avoid the hastle of typing out an outrageous amount of cards which is very very nice.

![](https://media3.giphy.com/media/l0ErFafpUCQTQFMSk/giphy.gif)

## Bonus Missions

1. **Super Bonus**: Create the game of [war](https://bicyclecards.com/how-to-play/war/).