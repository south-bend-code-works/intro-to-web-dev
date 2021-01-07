---
layout: default
---

# Introduction to JavaScript (JS): Event Listeners

## Goal
TO DO

## Overview
TO DO

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