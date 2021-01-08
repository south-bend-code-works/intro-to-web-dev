---
layout: default
---

# Project: Blackjack

## Goal
At the end of this project, you should have created a fully functioning game of black jack using our deck of cards.

## Overview
The game of blackjack is a gambling card game where players compete against a dealer to try to get closest to 21 without going over. While blackjack includes gambling and the exchange of chips, we won't focus on that today. We simply want to do the following:

- Create a deck of 52 cards
- Shuffle the deck
- Deal 2 cards to both dealer and player
- Show cards on screen
- Declare winner and restart

## Steps

### Setup

In order to start your page, you will need a new folder and a new file. Go to your desktop and create a new folder called `blackjack`. Then, open up VS Code and create a new file called `index.html` and save it inside of your `blackjack` folder.

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

After copying and pasting that into the file, go to the folder `blackjack` on you desktop, open it, right-click on `index.html`, and choose to open in your browser. Confirm that you can see `Hello world!`. If so, you are ready to get started.

### Creating a deck

Let's start by creating a deck of cards in JavaScript. A deck has 52 cards which are made up of 4 suits with 13 values within each suit. There are several ways we could represent this deck of cards in JS. For our purposes, I believe the easiest way for us to represent the deck is to use both an **arrays** and **objects**. 

Each individual card will be an **object** with 2 **key**/**value** pairs, the **suit** (`"hearts", "diamonds"`, etc.) and the **value** (`1`, `2`,). We are going to create a **object** for each card and then put all 52 cards into an **array**. This will allow us to do things like shuffle and deal cards without much work.

So, when it comes to making the individual card objects, we can do 1 of 2 things:
1. We manually type out each card. (Nope)
2. We use 2 **for** loops to create the 52 cards quickly and easily. (Yep)

Alright, so let's create a **function** that will build us a new deck. Let's call it `buildDeck`. `buildDeck` will need to return an **array** of 52 card objects. Let's include some of the parts of the **function** we know will be in there. Create a **variable** deck in `buildDeck` called `newDeck` that is an empty **array** and let's have our **function** return `newDeck`.

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

Here the **values** are either a string or a number. However, in the code with the double loops, the card object instead looks like this:

```
var card = {
  suit: suit,
  value: value,
}
```

It may looks strange since the words `suit` and `value` are being repeated but the same thing is going on in both of the previous examples. The only difference is that, in the second one, the second instances of `suit` and `value` are parameters that represent whatever element the loops are on. Take some time on this until it makes sense.

Cool! Now that we have created a **loop** within a **loop**, used those loops to create card **objects**, and then `push`ed those card **objects** onto an **array**, we have a function that returns a full deck! This is a great start. Copy and paste the following code to see the deck printed in the console:

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

### Shuffle the deck

We have created a function that returns a full deck of cards. The only bummer about the deck is that the cards are all in order. So, when we go to deal from the top of the deck, it will always be the `1` of `"heart"`. This isn't fun.

Similar to `.includes` or `.forEach`, JS has another function **arrays** can use which is `.sort`. Just like `.forEach`, `.sort` is expecting us to give it a **function**. Unlike `.forEach`, which need to be given a **function** that has one parameter, we need to give `.sort` a **function** that has 2 parameters. These parameters represent any 2 elements in the **array**. What we need to do with these 2 elements is to indicate how the **array** we are working with should be sorted. Let's look at an example:

```
var arr = [2,1,3,5]

var sortFunc = (num1, num2) => {
  var value
  if (num1 > num2) {
    value = 1
  } else {
    value = -1
  }
  return value
}

arr.sort(sortFunc)

// value of arr is [1, 2, 3, 5]
```

Hm. That all looks pretty strange. Let's break it down bit by bit.

Let's start with the things we know. The variable `arr` isn't too bad, just an **array** of numbers.

Next, we have a **function** called `sortFunc`. It takes in 2 parameters, `num1` and `num2`. We know these parameters will be numbers because `arr` is an array of numbers. Then, we have a variable `value` that is `undefined` to start. Then, we have a **conditional block**. The first conditional asks *is `num1` greater than `num2`?* If this is `true`, then `value` is equal to `1`. Otherwise, `value` is equal to `-1`. At the end of this **function**, `value` is returned.

Finally, we have `arr.sort` called with the **function** we just talked about. So, let's look deeper into `sortFunc`.

`sortFunc` is a **compare function**. **Compare functions** take in 2 elements (let's call them `a` and `b`) from the array (`arr` in this case), compares them, and then return either a positive or negative number. If the number returned from the **compare function** is negative, we want to sort `a` to a lower index than `b`. If the number returned from the **compare function** is positive, we want to sort `a` to a higher index than `b`.

For example, all I did was change the `>` to a `<` in the following example and the result is the exact opposite:

```
var arr = [2,1,3,5]

var sortFunc = (num1, num2) => {
  var value
  if (num1 < num2) {
    value = 1
  } else {
    value = -1
  }
  return value
}

arr.sort(sortFunc)

// value of arr is [5, 3, 2, 1]
```

Let's look at one more example to see if we can make a little more sense of this.

```

var cards = [
  {suit: "heart", number: 5}, 
  {suit: "spade", number: 10},
  {suit: "heart", number: 3},
]

var sortFunc = (card1, card2) => {
  var result

  if (card1.number > card2.number) {
    result = 1
  } else {
    result = -1
  }

  return value
}

arr.sort(sortFunc)

// value of arr is [{suit: "heart", number: 3}, {suit: "heart", number: 5}, {suit: "spade", number: 10}]
```
Similar to the previous example, we have an **array** (this time called `cards`), a **compare function** called `sortFunc`, and then we use `.sort` on the **array** using `sortFunc`.

Just like last time, `sortFunc` takes in 2 arguments. Before, the arguments were numbers because the **array** we were sorting was made only of numbers. This time, the **array** is made of **objects** that are cards. So, the 2 arguments we give `sortFunc` will be cards. We are sorting the cards only by their **key** `number`. We can tell this because the **conditional** `card1.number > card2.number` is comparing one `card`'s `number` to the other `card`'s `number`. The cards will be sorted be their `number`s as can be seen at the end of the code where we see the value of `arr`.

This might not make a ton of sense and that's okay. We don't have to go to deep into this. We just need a gist of what `.sort` does so that we can use it to shuffle our `deck`.

What is interesting is that we just walked through how to use `.sort` to put an array in an order that makes sense. We arranged an array of numbers to be from smallest to largest and vice versa. We also sorted an array of cards so that their `number`s ranged from loweset to highest.

However, with shuffling, we are hoping to do the opposite. We want the cards to be sorted randomly. That's what shuffling is.

We know that when using `.sort` on an array, we give it a **compare function** that returns a 1 or a -1 which determines the order. If we want the cards to be shuffled, we need to create a **compare function** that returns a 1 or -1 randomly. But how do we get randomness in JavaScript?

JavaScript has many things already built into it to make our lives easier. One thing that is tricky to do that JS makes easy is to produce a **random** number. It looks like this:

```
var randomNum = Math.random()

// value of randomNum is 0.1461854585231066
```

That value of `randomNum` was `0.1461854585231066` only that time. If we were to run that code again, it would be another number.

The number that `Math.random()` produces will always be greater than or equal to `0` and less than `1`. So, how do we leverage this `Math.random()` to create a **compare function** that randomly returns `1` and `-1`?

Since `Math.random()` produces a number that is `>= 0` and `< 1`, let's choose a number in the middle so that it is above that number half the time and below that number half the time. That number looks like it will be `.5`.

Now, we just need to create a **functimn** named `shuffle`. It should have one parameter, `deck`, which is an array that we will sort randomly (a.k.a. `shuffle`). We should have a variable in this **function** called `sortFunc` that randomly returns a `1` or a `-1` like we described above. Then, is should use `.sort` on the `deck` using the `sortFunc`. Then, the **function** should return `deck`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <script>

  ...

  var shuffle = (deck) => {
    // we declare 2 parameters here even though we won't use them since we are using Math.random() to deteremine 1 or -1 instead of these values
    var sortFunc = (card1, card2) => { 
      var result

      if ( Math.random() > .5 ) {
        result = 1
      } else {
        result = -1
      }

      return result
    }

    deck.sort(sortFunc)

    return deck
  }

  </script>
</html>
```

If you want, use the functions we've built to create a deck, shuffle it, then use `console.log` to see it in you console.

Whew. Between `.sort` and **random** numbers, that can be a lot to take in. Feel free to take your time and really try and understand what is generally happening. If you can get the gist of this, you are doing great.

### Dealing cards

Wow! We have now built functions that can create a deck and shuffle a deck! Now that we have these functionalities, let's get the game actually going.

First, just because we have the functions to do these things doesn't mean we actually have a deck of cards yet. So, at the top of our code, let's create a **variable** named `deck`. By placing it here, we will be able to use this variable everywhere else in our code. We don't have to assign anything to it yet. Just creating the variable is enough.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <script>

    var deck

    ...

  </script>
</html>
```

Okay, so now that we have a variable named `deck`, let's create a function named `startGame` that create a new deck, shuffles that deck, and then assigns that shuffled deck to our variable `deck`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <script>

    var deck

    ...

    var startGame = () => {
      var newDeck = buildDeck()
      var shuffledNewDeck = shuffle(newDeck)
      deck = shuffledNewDeck
    }

  </script>
</html>
```

Now that we have a function that assigns a new, shuffled deck to `deck`, let's call that function at the bottom of our code so it runs automatically when the page loads.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <script>

    var deck

    ...

    var startGame = () => {
      var newDeck = buildDeck()
      var shuffledNewDeck = shuffle(newDeck)
      deck = shuffledNewDeck
    }

    startGame()

  </script>
</html>
```

Alright, so at this point, we have a new shuffled deck assigned to `deck` whenever the page loads. Nice.

While the actual game of blackjack includes rounds and decisions about whether or not to receive more cards from the dealer, our massively simplified version will simply have both the dealer and the player get 2 cards each. So, let's create 2 **variables** in our code that will represent the cards belonging to the dealer and player. Let's call them **dealerCards** and **playerCards**. They do not need to be assign values yet.


<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <script>

    var deck

    var dealerCards
    var playerCards

    ...

  </script>
</html>
```

Since both the player and the dealer will need 2 cards from the deck each, let's create a function that takes the top 2 cards from the deck and returns them.

When getting these cards, we might think we want to use `deck[0]` and `deck[1]` to get the top 2 values from the deck. However, while this would get those values, it doesn't remove those elements from the array. It simply reads those values. We want to actually remove those values from the deck and use them elsewhere. The way to do this is to use `.shift`. Below is an example:

```
var arr = [1,2,3,4,5]

var num = arr.shift()

// value of num is 1
// value of arr is [2,3,4,5]
```

In the example above, we can see that by using `.shift`, we removed the first value from `arr` and assigned it to `num`. Similarly, in our function that we are going to make that takes the top 2 cards and returns them, we are going to want to use `.shift`.

So, create a function named `get2Cards`. It will have no parameters. In `get2Cards`, it should have 2 variables, `card1` and `card2`. We should use `.shift` on `deck` to get these values. Then, put these values into an **array** and return it.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <script>

    ...

    var get2Cards = () => {
      var card1 = deck.shift()
      var card2 = deck.shift()
      
      var cards = [card1, card2]

      return cards
    }

    ...

  </script>
</html>
```

Nice! Now that we have a function that can deal us 2 cards, let's use it to assign 2 cards to both **dealerCards** and **playerCards**. We are going to want this to happen in our function `startGame` since we will want both dealer and player to be dealt 2 cards every game.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <script>

    ...
    
    var startGame = () => {
      var newDeck = buildDeck()
      var shuffledNewDeck = shuffle(newDeck)
      deck = shuffledNewDeck

      dealerCards = get2Cards()
      playerCards = get2Cards()
    }

    ...

  </script>
</html>
```

Cool! Feel free to use `console.log` underneath our new code to check the values of **dealerCards** and **playerCards** to make sure both of those variables have an array of 2 cards assigned to them.

### Show cards on screen

This is great. We have dealt 2 random cards to both our dealer and player. But we haven't created any HTML to show these cards at all. Let's make that happen.

In order to show these cards on the screen, we first need write some HTML so that we can reference it and then change the `.innerHTML`.

First, I'm going to create a `div` with the class `game-area`. This just signifies where in the HTML we can expect the entirety of the game to take place.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    
    <div class="game-area">

    </div>

  </body>
  <script>
    ...
  </script>
</html>
```

Now that we have a `game-area`, let's think about what areas the game will have. We have 2 characters, the dealer and the player. So, let's add 2 `div`s to `game-area` called with the class `character`. Within both of those `character` `div`s, we will need 2 things, the area for the `title` of our `character` and the `card-area` where we will display the value of our cards. Within the `div` tags with the class `title`, put the word `Dealer` in the first one and `Player` in the second. Lastly, within both `card-area`s, we will need to `card` `div`s. We need to give all 4 of these `card` `div`s `id`s so that we can use `.innerHTML` to display the values individual cards. For `id`s for these `card` `div`s, let's use the name of the character and then the index of the card. So, the 4 `id`s will be `dealer-0`, `dealer-1`, `player-0`, and `player-1`.

Let's add all of these `div`s with appropriate classes and `id`s.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    
    <div class="game-area">

      <div class="character">
        <div class="title">Dealer</div>
        <div class="card-area">
          <div id="dealer-0" class="card"></div>
          <div id="dealer-1" class="card"></div>
        </div>
      </div>

      <div class="character">
        <div class="title">Player</div>
        <div class="card-area">
          <div id="player-0" class="card"></div>
          <div id="player-1" class="card"></div>
        </div>
      </div>

    </div>

  </body>
  <script>
    ...
  </script>
</html>
```

Now, if we reload our page, it will look something like this:

![]({{ site.baseurl }}/assets/img/module2/bj-1.png)

Now that is just gorgeous.

Before we actually put values in our `card`s, let's make our `card`s look a little more like cards. In the CSS, I'm going to use the selector `.card` and add a black, solid, thin border along with a `border-radius` of `16px`. 

After refreshing, I realize that the `card`s look like very long lines the width of the screen. So, I'll add a `height` of `150px` and `width` of `90px` to my `card` selector to see if that helps.

That definitely helps but the cards are all smooshed together. I'll add `16px` of margin to the bottom of the `card`s and call it good.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>

      .card {
        border: thin solid black;
        border-radius: 16px;
        height: 150px;
        width: 90px;
        margin-bottom: 16px;
      }

    </style>
  </head>
  <body>
    ....
  </body>
  <script>
    ...
  </script>
</html>
```

While it is still a wildly unattractive webpage, it's good enough to keep moving.

So, we now we have somewhere to display the card values. The last thing to do is to actually put in the values!

In our JavaScript, we are at the point where both characters already have their cards in an array. Let's create a function that takes those arrays and uses `.innerHTML` to put the values of those cards into the HTML.

First, let's start a function named `displayCards`. In `displayCards`, we are going to need to reference individual `card`s using there `id`s (remember `document.getElementById`). After referencing the `card`, we will need to use `.innerHTML` to input of the the cooresponding cards. Each card object in the arrays have a `value` and a `suit`. The string we should put into each `card` is `card.value + " of " + card.suit`.

Then, `displayCards` should be called in the function `startGame` right after both `dealerCards` and `playerCards` are assigned values.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <script>

    ...

    var displayCards = () => {

      var dealerCard0 = dealerCards[0]
      document.getElementById("dealer-0").innerHTML = dealerCard0.value + " of " + dealerCard0.suit

      var dealerCard1 = dealerCards[1]
      document.getElementById("dealer-1").innerHTML = dealerCard1.value + " of " + dealerCard1.suit

      var playerCard0 = playerCards[0]
      document.getElementById("player-0").innerHTML = playerCard0.value + " of " + playerCard0.suit

      var playerCard1 = playerCards[1]
      document.getElementById("player-1").innerHTML = playerCard1.value + " of " + playerCard1.suit

    }
    
    var startGame = () => {
      var newDeck = buildDeck()
      var shuffledNewDeck = shuffle(newDeck)
      deck = shuffledNewDeck

      dealerCards = get2Cards()
      playerCards = get2Cards()
      displayCards()
    }

    ...

  </script>
</html>
```

If you refresh your webpage, it will hopefully look something like this:

![]({{ site.baseurl }}/assets/img/module2/bj-2.png)

I mean, holy smokes, it's gorgeous! But just to make it slightly less awful, let's center the words within the `card`. Let's use the `card` CSS selector to make all `card`s grids with their items vertically and horizontally aligned.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>

      .card {
        border: thin solid black;
        border-radius: 16px;
        height: 150px;
        width: 90px;
        margin-bottom: 16px;
        display: grid;
        align-items: center;
        justify-items: center;
      }

    </style>
  </head>
  <body>
    ....
  </body>
  <script>
    ...
  </script>
</html>
```

Well, it's still hideous but we're rolling with it.

### Declare winner and restart

Wow! We can now endlessly refresh the page and get new cards for both of our characters every time. Pretty neat stuff! Now to make it an actual game.

In actual blackjack, scoring has some complexity to it. All face cards are worth then, aces can be either 1 or 11, etc. In our very simple version of the game, to find a winner, we are simply going to add together the value of both characters' cards. The winner will be the character with the higher sum. If it is a tie, the dealer will be declared the winner.

So, let's create a function called `declareWinner`. The first thing we need to do in this function is to find the totals for both our dealer and player. I'm going to use `.forEach` to accomplish this but there are several acceptable ways of doing this. Store the sum for each character in variables named `dealerTotal` and `playerTotal`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <script>

    ...

    var declareWinner = () => {
      var dealerTotal = 0
      var playerTotal = 0

      dealerCards.forEach((card) => {
        dealerTotal = dealerTotal + card.value
      })

      playerCards.forEach((card) => {
        playerTotal = playerTotal + card.value
      })
    }

    ...

  </script>
</html>
```

Now that we have the totals, let's use another nice built-in JavaScript method called `alert`. At the bottom of `declareWinner`, write `alert(dealerTotal + " " + playerTotal)`. Then, after a refresh, you should have a pop-up with 2 numbers, one for each of the totals of your characters' card values. Pretty cool, right?

Since we can declare things using an `alert` message, let's craft 2 messages: 1 for when the player wins and 1 for when the dealer wins. We are going to need a variable `message` and 2 conditional statements that we can use to assign crafted strings to `message`. If the player wins, my message is going to be `"Cool! Player beats dealer, " + playerTotal + " to " + dealerTotal + "."`. Otherwise my message is going to be `"Bummer. Dealer won, " + dealerTotal + " to " + playerTotal + "."`. Then, I'm going to use `alert` to display my message.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <script>

    ...

    var declareWinner = () => {
      var dealerTotal = 0
      var playerTotal = 0

      dealerCards.forEach((card) => {
        dealerTotal = dealerTotal + card.value
      })

      playerCards.forEach((card) => {
        playerTotal = playerTotal + card.value
      })

      var message
      if (playerTotal > dealerTotal) {
        message = "Cool! Player beats dealer, " + playerTotal + " to " + dealerTotal + "."
      } else {
        message = "Bummer. Dealer won " + dealerTotal + " to " + playerTotal + "."
      }

      alert(message)
    }

    ...

  </script>
</html>
```

Now that we have our `declareWinner` function made, let's call it at the bottom of our `startGame` function since at this point all characters have their cards and the cards have been displayed.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <script>

    ...

    var startGame = () => {
      var newDeck = buildDeck()
      var shuffledNewDeck = shuffle(newDeck)
      deck = shuffledNewDeck

      dealerCards = get2Cards()
      playerCards = get2Cards()
      displayCards()
      declareWinner()
    }

    ...

  </script>
</html>
```

Hm. Something weird is happening. My cards aren't evening being displayed before the `alert` is shown. I'm going to delay the `declareWinner` call so that I can see the cards before the winner is declared. The way we delay the call of a function is to use `setTimeout`. It is similar to `setInterval` which we have used before in our Virtual Pet. They both take 2 things, a reference to a function and an amount of time in milliseconds. The difference is this: `setInterval` runs a function over and over again, using the time as the amount of time in between function runs while `setTimeout` only runs the given function once with the time given to it as the delay before the function is run.

Example:

```
var sayHi = () => {
  console.log("Hi!")
}

setInterval(sayHi, 2000) // will run sayHi every 2 seconds
setTimeout(sayHi, 500) // waits a half second before running sayHi only one time and then being done
```

Okay, now that we know what `setTimeout` is, let's use it in our function `startGame`. In place of the line that calls `declareWinner`, let's instead use `setTimeout`, passing to it the reference to the function `declareWinner` and the time `2000`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <script>

    ...

    var startGame = () => {
      var newDeck = buildDeck()
      var shuffledNewDeck = shuffle(newDeck)
      deck = shuffledNewDeck

      dealerCards = get2Cards()
      playerCards = get2Cards()
      displayCards()
      setTimeout(declareWinner, 2000)
    }

    ...

  </script>
</html>
```

Cool! Now there is a delay where I can see the cards for 2 seconds before an alert comes up to declare the winner.

The last thing we want to do is to offer a restart to the game. Similar to `alert`, another method exists in JavaScript that allows us to prompt the user and make decisions based on the user's response. The method is `confirm` and it takes one argument, a string, where we can prompt the user to which they will have 2 buttons to respond, `Cancel` and `OK` (which are defaults that we can't change). If the user selects `OK`, `confirm` will return `true`, otherwise, `false`.

Let's see an example in action:

```
var answer = confirm("Press OK to be greeted.")

if (answer) {
  console.log("Well, howdy!")
} else {
  console.log("Fine, no hello for you.")
}

// if user selects `OK`, "Well, howdy!" will be printed to the console
// if user selects `Cancel`, "Fine, no hello for you." will be printed to the console
```

Now that we know what `confirm` is, we can use to potentially restart the game. What we can do is use `confirm` at the bottom of `declareWinner` to prompt the user with `"Would you like to play again? Press OK to restart the game."`. If so, we run `startGame` and the whole thing begins again.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <script>

    ...

    var declareWinner = () => {
      var dealerTotal = 0
      var playerTotal = 0

      dealerCards.forEach((card) => {
        dealerTotal = dealerTotal + card.value
      })

      playerCards.forEach((card) => {
        playerTotal = playerTotal + card.value
      })

      var message
      if (playerTotal > dealerTotal) {
        message = "Cool! Player beats dealer, " + playerTotal + " to " + dealerTotal + "."
      } else {
        message = "Bummer. Dealer won, " + dealerTotal + " to " + playerTotal + "."
      }

      alert(message)

      var answer = confirm("Would you like to play again? Press OK to restart the game.")
      if (answer) {
        startGame()
      }
    }

    ...

  </script>
</html>
```

Nice! Now we can play endlessly if we so desire.

### Complete Solution

```
<!DOCTYPE html>
<html>
  <head>
    <style>

      .card {
        border: thin solid black;
        border-radius: 16px;
        height: 150px;
        width: 90px;
        margin-bottom: 16px;
        display: grid;
        align-items: center;
        justify-items: center;
      }
      
    </style>
  </head>
  <body>
    
    <div class="game-area">

      <div class="character">
        <div class="title">Dealer</div>
        <div class="card-area">
          <div id="dealer-0" class="card"></div>
          <div id="dealer-1" class="card"></div>
        </div>
      </div>

      <div class="character">
        <div class="title">Player</div>
        <div class="card-area">
          <div id="player-0" class="card"></div>
          <div id="player-1" class="card"></div>
        </div>
      </div>

    </div>

  </body>
  <script>

    var deck
    var dealerCards
    var playerCards

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
    
    var shuffle = (deck) => {
      // we declare 2 parameters here even though we won't use them since we are using Math.random() to deteremine 1 or -1 instead of these values
      var sortFunc = (card1, card2) => { 
        var result

        if ( Math.random() > .5 ) {
          result = 1
        } else {
          result = -1
        }

        return result
      }

      deck.sort(sortFunc)

      return deck
    }

    var get2Cards = () => {
      var card1 = deck.shift()
      var card2 = deck.shift()

      var cards = [card1, card2]

      return cards
    }

    var displayCards = () => {

      var dealerCard0 = dealerCards[0]
      document.getElementById("dealer-0").innerHTML = dealerCard0.value + " of " + dealerCard0.suit

      var dealerCard1 = dealerCards[1]
      document.getElementById("dealer-1").innerHTML = dealerCard1.value + " of " + dealerCard1.suit

      var playerCard0 = playerCards[0]
      document.getElementById("player-0").innerHTML = playerCard0.value + " of " + playerCard0.suit

      var playerCard1 = playerCards[1]
      document.getElementById("player-1").innerHTML = playerCard1.value + " of " + playerCard1.suit

    }

    var declareWinner = () => {
      var dealerTotal = 0
      var playerTotal = 0

      dealerCards.forEach((card) => {
        dealerTotal = dealerTotal + card.value
      })

      playerCards.forEach((card) => {
        playerTotal = playerTotal + card.value
      })

      var message
      if (playerTotal > dealerTotal) {
        message = "Cool! Player beats dealer, " + playerTotal + " to " + dealerTotal + "."
      } else {
        message = "Bummer. Dealer won, " + dealerTotal + " to " + playerTotal + "."
      }

      alert(message)

      var answer = confirm("Would you like to play again? Press OK to restart the game.")
      if (answer) {
        startGame()
      }
    }
    
    var startGame = () => {
      var newDeck = buildDeck()
      var shuffledNewDeck = shuffle(newDeck)
      deck = shuffledNewDeck

      dealerCards = get2Cards()
      playerCards = get2Cards()
      displayCards()
      setTimeout(declareWinner, 2000)
    }

    startGame()

  </script>
</html>
```

## Conclusion

Wow! We were able to apply our new knowledge of **arrays** and **objects** (along with a whole bunch of other new stuff) to make a card game. Sure, the game we made is wildly ugly and follows very few of the rules of blackjack but this should only deepen our appreciation for the complexity that comes with creating even seemingly simple games.

![](https://i.gifer.com/7O9a.gif)

## Bonus Missions

1. This thing is ugly. Add some styling to make the cards and table look like a poker table.
2. Add some more blackjack rules! Include hitting and betting.
