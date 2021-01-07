---
layout: default
---

# Introduction to JS: Event Listeners

## Goal

By the end of this lesson, the goal is to understand event listeners in JS and how to implement them to create more interactive webpages.

## Overview

Event listeners are powerful in their ability to receive input from the user and respond. We set up these listeners in the code and they just wait there until the user performs the event we are looking for and then responds with the instructions we give it. Pretty neat!

## Topics

### Recap on `onclick`

Before, when we have wanted to a button or other `div` to do something when being clicked, we have given the element the attribute `onclick` and set it equal to a function in our JS. Example below:

```
<!DOCTYPE html>
<html>

  <body>
    <button onclick="sayHello()">Click for a hello!</button>
  </body>

  <script>

    var sayHello = () => {
      alert("Hello!")
    }

  </script>
</html>
```

In the example above, we see some HTML in between our `body` tags and some JS between our `script` tags. 

Our HTML consists of one element, a `button`. Inside the opening tag of our `button`, we have the attribute `onclick` which is set to `sayHello()`. This means that when we click on the `button`, we will run the function `sayHello`.

We have seen this several times before but I wanted to bring this up as a reminder of our current way of handling for clicks before we dive into a new way.

## Event Listeners

When we use the ``