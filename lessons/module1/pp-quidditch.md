---
layout: default
---

# Practice Problem: Quidditch Cup 1.0

## Goal

Our goal for this project is to build an interactive, web-based version of Quidditch, a fictional sport invented by author J.K. Rowling for her fantasy book series Harry Potter. 

At the end of this activity, you will have built something similar to this:

![quidditch example]({{ site.baseurl }}/assets/img/module1/quidditch1.0-animated.gif)

## Overview

In prior the lessons, all of the HTML and CSS on our page was static, meaning that it stayed the same.  In this activity we will use JavaScript to manipulate our HTML and CSS to dynamically update our webpage and game.  Developers call this process of dynamically updating the HTML and CSS **manipulating the DOM** (Document Object Model).  

For example, when a player clicks on the Quaffle we need to increase the score of the game by 10 points.  We can accomplish this by changing the HTML that displays the score using JavaScript.

We will practice following concepts in this lesson:
* Visual Studio Code (VS Code)
* HTML, CSS
* JavaScript

## Instructions

### 1. Create a new project

* First, on your desktop, right-click and create a New Folder. Name it `quidditch-cup`.
* Open your new folder in VS Code. 
* In the toolbar at the top, under File, click New File. Save the file as `index.html`.
* Copy and paste the following starter code into your index.html file in VS Code:
  
```
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Quidditch Cup</title>
    <style>
      .brown {
        background-color: brown;
        color: white;
        padding: 3px;
        border-radius: 5px;
      }

      li {
        padding: 6px;
      }

      button {
        margin: 5px;
      }

      #gameboard {
        background-color: lightskyblue;
        height: 500px;
        width: 500px;
      }

      #quaffle {
        position: absolute;
        background-image: url("imgs/quaffle64x64.png");
        width: 64px;
        height: 64px;
        visibility: hidden;
        transition: 0.5s transform;
      }
    </style>
  </head>
  <body>
    <h1>Quidditch Cup</h1>
    <h2>Version 1.0</h2>
    <p>The object of the game of Quidditch is to score more the most points!</p>
    <h2>Rules</h2>
    <ol>
      <li>Clicking on the <span class="brown">Quaffle</span> earns <b>10 points</b>.</li>
      <li>Refresh your browser to restart the game</li>
    </ol>
    <h3>Score: <span id="scoreboard">No Score Yet</span></h3>

    <button>New Game</button>

    <div id="gameboard">
      <div id="quaffle"></div>
    </div>

    <script>
      // All of our JavaScript will be written inside this script tag.

    </script>
  </body>
</html>
```

#### Try it out
* Save the file and go to your desktop where you can see the folder `quidditch-cup`. Click into it and right-click on the `index.html` and open with Chrome (or whatever browser you have).
* You should see our `Quidditch Cup` application, however clicking on _new game_ shouldn't do anything yet.

### 2. Download and add the supporting files we will need to your project folder
Download the images we will use in our game:
* Right-Click and download the following images 
* Save them in a new sub-folder, `imgs`, in your `quidditch-cup` project directory.

Quaffle            |  Golden Snitch
:-------------------------:|:-------------------------:
![]({{ site.baseurl }}/assets/img/module1/quidditch-assets/quaffle64x64.png)  |  ![]({{ site.baseurl }}/assets/img/module1/quidditch-assets/snitch64x64.png)


### 3. Make the `New Game` Button Work

Now we will add some JavaScript to start our game when the user clicks the `new game` button.

For each step below, write your code between the `<script></script>` tags in our index.html file.
* Define a variable, called _score_, and initialize it to 0.
  * We will use this to track the score for our player.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<script>
  var score = 0;
</script>
```

* Define a variable, _scoreboard_, and set it equal to the result of: `document.getElementById("scoreboard");`
  * This represents the HTML element with the ID of "scoreboard".
  * We will use this to update the the following html: `<span id="scoreboard">No Score Yet</span>`.
  * For example, if we wanted the score to be 1000 you could run the following JavaScript: `scoreboard.innerHTML = "1000"`

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<script>
  var score = 0;
  var quaffle = document.getElementById("quaffle");
</script>
```

* Define a variable, _quaffle_, and set it equal to the result of: `document.getElementById("quaffle");`
  * This variable is references the HTML element with the ID of "quaffle"
  * We will use this variable to modify the position of our quaffle div on the screen.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<script>
  var score = 0;
  var scoreboard = document.getElementById("scoreboard");
  var quaffle = document.getElementById("quaffle");
</script>
```

* Declare a new function, _startGame()_, it should:
  * Ensure the score is set to zero by:
    * setting our _score_ variable to 0
    * setting the innerHTML of our _scoreboard_ to _score_
  * Unhide the quaffle
    * set the css visibility attribute of our _quaffle_ div to visible in the DOM by:
      * quaffle.style.visibility = "visible";
      * notice that this was originally set to "hidden".

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<script>
  var score = 0;
  var scoreboard = document.getElementById("scoreboard");
  var quaffle = document.getElementById("quaffle");

  // Function that starts a new game of Quidditch!
  function startGame() {
    // Set the score to zero
    score = 0;
    scoreboard.innerHTML = score;

    // Make our quaffle objects visibile. Note that we initially set them to be invisible in our CSS above.
    quaffle.style.visibility = "visible";
  }
</script>
```

* In our HTML, we need to update our button so that it knows what to do when it's clicked.  
    * This is done using the onclick handler, to which we provide some javascript that we want to run.  
    * Modify your button's HTML to call our _startGame()_ function like such:
      * ```<button onclick="startGame()">New Game</button>```

#### Try it out

:-------------------------:|:-------------------------:
Once you've made your changes, refresh your browser and click on _new game_.  This should set the score to 0 and unhide our quaffle image on the page, though nothing will move yet. 

Hints:
  * You can see what code your browser is running by using the Developer Tools in Chrome to inspect the code.
  * You can also debug any errors you might be seeing.  For example, chrome might warn you if it cannot find the quaffle.png, which means you may have not downloaded it or placed it in the appropriate location.

| After clicking "New Game" your screen should look like this:
![new game]({{ site.baseurl }}/assets/img/module1/quidditch1.0-newgame.png)

### 4. Make the Quaffle Move

Now comes the fun part, let's update our JavaScript code to make our quaffle fly about on the screen.

To accomplish this we will introduce a handy JavaScript function: `setTimeout()`.  This is a function that takes two arguments.  The first argument is the name of another function we want to call.  The second argument is the amount of time in milliseconds we should wait before calling that function.  Note that 1000 milliseconds equals 1 second.

Now that we have learned about setTimeout, let's use it.  To do this we need to add the function called `moveQuaffle()` to our script.  The code for this function is included below for your convenience.

```
function moveQuaffle() {
  // Generate a random x,y position for our Quaffle
  let randY = Math.floor(Math.random() * 436 + 1); // 500 (the width of the game board) - 64 (the width of the quaffle) = 436 px
  let randX = Math.floor(Math.random() * 436 + 1);

  // Use CSS to animate the transition from our current position to the new position.
  quaffle.style.transform = `translate(${randX}px, ${randY}px)`; // Use a 'template literal' (backtick) to generate the string we need for our css animation.

  // If we had a move that hasn't completed, let's clear it so we can make a new one.
  clearTimeout(quaffleTimeoutID)
  
  // Move the Quaffle after so many seconds.
  quaffleTimeoutID = setTimeout(moveQuaffle, quaffleSpeed); // Note: we keep track of this timer by storing it in the quaffleTimeoutID variable in case we need to cancel the movement later.
}
```

Next, we need to add some variables that this function uses to animate the quaffle.  Add the following variables at the top of our script:
* A new variable, `quaffleSpeed`, that is set to 1500 milliseconds (1.5 seconds)
* A new variable, `quaffleTimeoutID`, with the following code: `var quaffleTimeoutID = null`.  We will use this in the next step.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<script>
  var score = 0;
  var scoreboard = document.getElementById("scoreboard");
  var quaffle = document.getElementById("quaffle");

  // Variables to help animate our quaffle.
  var quaffleSpeed = 1500; // speed in Milliseconds.
  var quaffleTimeoutID = null;

  // Function that starts a new game of Quidditch!
  function startGame() {
    // Set the score to zero
    score = 0;
    scoreboard.innerHTML = score;

    // Make our quaffle objects visibile. Note that we initially set them to be invisible in our CSS above.
    quaffle.style.visibility = "visible";
  }

  function moveQuaffle() {
    // Generate a random x,y position for our Quaffle
    let randY = Math.floor(Math.random() * 436 + 1); // 500 (the width of the game board) - 64 (the width of the quaffle) = 436 px
    let randX = Math.floor(Math.random() * 436 + 1);

    // Use CSS to animate the transition from our current position to the new position.
    quaffle.style.transform = `translate(${randX}px, ${randY}px)`; // Use a 'template literal' (backtick) to generate the string we need for our css animation.

    // If we had a move that hasn't completed, let's clear it so we can make a new one.
    clearTimeout(quaffleTimeoutID)
    
    // Move the Quaffle after so many seconds.
    quaffleTimeoutID = setTimeout(moveQuaffle, quaffleSpeed); // Note: we keep track of this timer by storing it in the quaffleTimeoutID variable in case we need to cancel the movement later.
  }
</script>
```

* Finally, we need to add one line of code in our startGame() function to call moveQuaffle().

<div class="hint">Hover for hint</div>

{: .hint-content}
```
  // Function that starts a new game of Quidditch!
  function startGame() {
    // Set the score to zero
    score = 0;
    scoreboard.innerHTML = score;

    // Make our quaffle objects visibile. Note that we initially set them to be invisible in our CSS above.
    quaffle.style.visibility = "visible";

    // move the quaffle
    moveQuaffle(); //ADD THIS LINE OF CODE TO START MOVING THE QUAFFLE.
  }
```

#### Try it out
Try it out in your browser.  You should see your quaffle flying about the screen.  

Pause and try and answer the following questions:
* Why does the quaffle keep moving about the screen as opposed to moving once and stoping?  See if you can identify the line of code that makes this animation repeat itself indefinitely.
* How would you increase or decrease the speed of the quaffle?

### 5. Update our Score each time we click on the Quaffle

It wouldn't be a game if we didn't keep track of the score.  Previously, we added an onclick handler to our new game button which make sense as people click buttons.  However, HTML actually allows us to add onclick handlers to any objects, including DIV objects.  In this case, we want to add an onclick handler for our quaffle, which is a div defined as: `<div id='quaffle>`.  Using onclick in this way we can take any action whenever the user successfully clicks on the quaffle.

When the quaffle is clicked you will:
* Increment our score by 10 points
* Immediately move the quaffle to a new location 

Modify our JavaScript in the following ways:

* Create a new function, _scoreQuaffle()_, that does the following:
  * Increments our _score_ variable by 10 points
  * Updates the _scoreboard_ on our webpage
  * Calls moveQuaffle() to immediately update the location of our quaffle.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<script>
  // Logic to score when the quaffle is clicked.
  function scoreQuaffle() {
    // 10 points for scoring the quaffle!
    score = score + 10;

    // Update the scoreboard
    scoreboard.innerHTML = score;

    // Move the Quaffle Immediately!
    clearTimeout(quaffleTimeoutID); // Cancel the previously planned movement of the Quaffle.
    moveQuaffle(); // Move the Quaffle Immediatly
  }
<script>
```

Modify our HTML Code:
* Add an onclick handler to the quaffle div.  It should call the scoreQuaffle() function.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<div id="gameboard">
  <div id="quaffle" onclick="scoreQuaffle()"></div>
</div>
```

#### Try it out
Try it out in your browser.  You should now be able to see the score increase and have a mostly complete game!  You can refresh your browser to reset the game and play again.

## Complete Solution

Congrats!  At this point you've built a fully functional game using Javascript to manipulate the DOM (aka our html and css).  In our in-class live session we take a deeper dive into this solution and extend the game with new features.  

Here is all the completed code, all together, for version 1.0 of our Quidditch Cup game:

<div class="hint">Complete Solution</div>

{: .hint-content}
```
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Quidditch Cup</title>
    <style>
      .brown {
        background-color: brown;
        color: white;
        padding: 3px;
        border-radius: 5px;
      }

      li {
        padding: 6px;
      }

      button {
        margin: 5px;
      }

      #gameboard {
        background-color: lightskyblue;
        height: 500px;
        width: 500px;
      }

      #quaffle {
        position: absolute;
        background-image: url("imgs/quaffle64x64.png");
        width: 64px;
        height: 64px;
        visibility: hidden;
        transition: 0.5s transform;
      }
    </style>
  </head>
  <body>
    <h1>Quidditch Cup</h1>
    <h2>Version 1.0</h2>
    <p>The object of the game of Quidditch is to score more the most points!</p>
    <h2>Rules</h2>
    <ol>
      <li>Clicking on the <span class="brown">Quaffle</span> earns <b>10 points</b>.</li>
      <li>Refresh your browser to restart the game</li>
    </ol>
    <h3>Score: <span id="scoreboard">0</span></h3>

    <button onclick="startGame()">New Game</button>

    <div id="gameboard">
      <div id="quaffle" onclick="scoreQuaffle()"></div>
    </div>

    <script>
      // Variables accessible anywhere inside this <script> tag.
      var score = 0;
      var scoreboard = document.getElementById("scoreboard");
      var quaffle = document.getElementById("quaffle");

      // Variables to help animate our quaffle.
      var quaffleSpeed = 1500; // speed in Milliseconds.
      var quaffleTimeoutID = null;

      // Function that starts a new game of Quidditch!
      function startGame() {
        // Reset the score board
        score = 0;
        scoreboard.innerHTML = score;

        // Our quaffle is, by default, invisible.  We need to unhide it as we start our game.
        quaffle.style.visibility = "visible";
        
        // Move the ball
        moveQuaffle();
      }

      // Logic to move the Quaffle
      function moveQuaffle() {
        // Generate a random x,y position for our Quaffle
        let randY = Math.floor(Math.random() * 436 + 1); // 500 (the width of the game board) - 64 (the width of the quaffle) = 436 px
        let randX = Math.floor(Math.random() * 436 + 1);

        // Use CSS to animate the transition from our current position to the new position.
        quaffle.style.transform = `translate(${randX}px, ${randY}px)`; // Use a 'template literal' (backtick) to generate the string we need for our css animation.

        // Plan to move the Quaffle again in a second or so if the player fails to clicks on it.
        quaffleTimeoutID = setTimeout(moveQuaffle, quaffleSpeed);
      }

      // Logic to score when the quaffle is clicked.
      function scoreQuaffle() {
        // 10 points for scoring the quaffle!
        score = score + 10;

        // Update the scoreboard
        scoreboard.innerHTML = score;

        // Move the Quaffle Immediately!
        clearTimeout(quaffleTimeoutID); // Cancel the previously planned movement of the Quaffle.
        moveQuaffle(); // Move the Quaffle Immediatly
      }
    </script
  </body>
</html>
```

## Bonus Mission 
Feel free to try and enhance our game in the following ways:
* Add the a timer so that the game ends after 15 seconds
* Add a Golden Snitch, that when captured gives you 150 points and ends the game
* Add the ability to track your highest score

Keep in mind that while there are no grades for this program, your projects will speak to the work you can do should you choose to use them as a part of your resume.


