---
layout: default
---

# Overview 

## Agenda
1. Using functions and basic logic in JavaScript
2. Learn the Document Object Model (DOM) and combine HTML, CSS, and JavaScript to build interactive websites. 
3. Small Group Exercise: Quidditch 2.0
4. Hosting Quidditch 2.0 on Github
5. (last 5 minutes)
    - Review Final Project Part 2 
    - Talk about the upcoming lab and it's format

## Zoom Links

### Section 1 (10am to 12pm)
<https://notredame.zoom.us/j/96545079849?pwd=K3psL1J4Q3FUNmxCbmpSa0pTbm9ndz09>

**Meeting ID: 965 4507 9849**

**Passcode: 835805**


### Section 2 (1pm to 3pm) 
<https://notredame.zoom.us/j/99670056329?pwd=OXRmSFNERU45Vi9ndkpJNUpGTFU1QT09>

**Meeting ID: 996 7005 6329**

**Passcode: 781595**

### Section 3 (4pm to 6pm) 
<https://notredame.zoom.us/j/92241686868?pwd=aHBiTmdOM25Eak52UEtOQU5XeDJvZz09>

**Meeting ID: 922 4168 6868**

**Passcode: 122449**

## Quidditch 2.0 Instructions
In the second half of this live session you will break into small groups and individually enhance Quidditch 1.0 in the following ways:

### Features for 2.0:

1.  Update your the HTML that gives the rules of the game to include:
    * Rules 2 & 3 from the solution image at the bottom of this page.

2.  Add the Golden Snitch.
    * Clicking the golden snitch earns 150 points AND ends the game.
    * The Snitch should be smaller than the actual image size, 32x32 px.  Use CSS to accomplish this.
    * The Snitch should be faster than the quaffle.
    * Hint: This will need a function similar to moveQuaffle().

3. Add a time limit to the game
    * Automatically End the Game after 15 seconds.
    * Show the time remaining in the game on the screen.
    * Hint: You should create a new function called updateTimer() that uses setTimeout() to call itself every second and update the time remaining in your HTML.

4. Add a background soundtrack to the game
    * Use the HTML5 Audio Tag
    * Download the background audio track here (or use your own!):
        * <a href="{{ site.baseurl }}/assets/img/module1/quidditch-assets/prologue.wav">prologue.wav</a>
        * Right click, and Save as prologue.wav in a new sub-folder inside your main quidditch project folder called *sound*.

Your final game should look like this:

![quidditch example]({{ site.baseurl }}/assets/img/module1/quidditch2.0-animated.gif)

## Solution code

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Quidditch</title>
    <style>
      .gold {
        background-color: gold;
        color: darkslategrey;
        padding: 3px;
        border-radius: 5px;
      }

      .brown {
        background-color: brown;
        color: white;
        padding: 3px;
        border-radius: 5px;
      }

      li {
        padding: 6px;
      }

      h1 {
        display: inline-block;
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

      #snitch {
        position: absolute;
        background-image: url("imgs/snitch64x64.png");
        background-size: 100% 100%;
        width: 32px;
        height: 32px;
        visibility: hidden;
        transition: 0.5s transform;
      }
    </style>
  </head>
  <body>
    <h1>Quidditch Cup 2.0</h1>
    <div></div>
    <audio src="sound/prologue.wav" controls autoplay>
      <p>If you are reading this, it is because your browser does not support this awesome audio track.</p>
    </audio>
    <p>The object of the game of Quidditch is to score more the most points!</p>
    <h2>Rules</h2>
    <ol>
      <li>Clicking on the <span class="brown">Quaffle</span> earns <b>10 points</b>.</li>
      <li>Clicking on the <span class="gold">Golden Snitch</span> earns <b>150 points</b> and <b>ends the game</b>.</li>
      <li>The game will automatically end after <b>15 seconds</b> if the Golden Snitch is not captured.</li>
    </ol>
    <h3>Score: <span id="scoreboard">0</span></h3>
    <h3>Time Remaining: <span id="timer">15</span></h3>

    <button onclick="startGame()">New Game</button>

    <div id="gameboard">
      <div id="quaffle" onclick="scoreQuaffle()"></div>
      <div id="snitch" onclick="scoreSnitch()"></div>
    </div>

    <script>
      // Variables accessible anywhere inside this <script> tag.
      var score = 0;
      var gameboard = document.getElementById("gameboard");
      var quaffle = document.getElementById("quaffle");
      var snitch = document.getElementById("snitch");
      var scoreboard = document.getElementById("scoreboard");
      var timer = document.getElementById("timer");

      var secondsRemaining = 0;

      var quaffleTimeoutID = null;
      var snitchTimeoutID = null;
      var secondsRemainingTimeoutID = null;
      var gameTimeoutID = null;

      // Constants. Change these values to make the gameplay different 
      var quaffleSpeed = 1500; // speed in Milliseconds.
      var snitchSpeed = 1000; // speed in Milliseconds.
      var gameLength = 15000; // gameLength in milliseconds.

      // Function that starts a new game of Quidditch!
      function startGame() {
        // Reset the score board
        score = 0;
        scoreboard.innerHTML = score;

        // End our game after 15 seconds
        gameTimeoutID = setTimeout(endGame, gameLength); // The setTimeout() method calls a function or evaluates an expression after a specified number of milliseconds.

        // Print the time remaining on the page
        secondsRemaining = gameLength / 1000; // Divide by 1000 to convert milliseconds to seconds.
        updateSecondsRemaining();

        // Make our quaffle and snitch objects appear. Notice that we initially set them to be invisible in our CSS.
        quaffle.style.visibility = "visible";
        snitch.style.visibility = "visible";

        // Move the balls
        moveQuaffle();
        moveSnitch();
      }

      // Logic to move the Quaffle
      function moveQuaffle() {
        // Generate a random x,y position for our Quaffle
        let randY = Math.floor(Math.random() * 436 + 1); // 500 (the width of the game board) - 64 (the width of the quaffle) = 436 px
        let randX = Math.floor(Math.random() * 436 + 1);

        // Use CSS to animate the transition from our current position to the new position.
        quaffle.style.transform = `translate(${randX}px, ${randY}px)`; // Use a 'template literal' (backtick) to generate the string we need for our css animation.

        // Cancel any previously planned movement of the Quaffle.
        clearTimeout(quaffleTimeoutID); 

        // Plan to move the Quaffle again in a second or so if the player fails to clicks on it.
        quaffleTimeoutID = setTimeout(moveQuaffle, quaffleSpeed);
      }

      // Logic to move the Snitch
      function moveSnitch() {
        let randY = Math.floor(Math.random() * 468 + 1); // 500 (the width of the game board) - 32 (the width of the snitch)= 468 px
        let randX = Math.floor(Math.random() * 468 + 1);

        snitch.style.transform = `translate(${randX}px, ${randY}px)`;

         // Cancel any previously planned movement of the snitch.
         clearTimeout(snitchTimeoutID); 

        snitchTimeoutID = setTimeout(moveSnitch, snitchSpeed);
      }

      // Logic to score when the quaffle is clicked.
      function scoreQuaffle() {
        // 10 points for scoring the quaffle!
        score = score + 10;

        // Update the scoreboard
        scoreboard.innerHTML = score;

        // Move the Quaffle Immediately!
        moveQuaffle(); // Move the Quaffle Immediatly
      }

      // Logic to score AND end the game when the snitch is clicked.
      function scoreSnitch() {
        score = score + 150;
        scoreboard.innerHTML = score;

        // End the game if the snitch is clicked.
        endGame();
      }

      // Function to update the timer
      function updateSecondsRemaining() {
        timer.innerHTML = secondsRemaining;

        if (secondsRemaining > 0) {
          secondsRemaining = secondsRemaining - 1;
          secondsRemainingTimeoutID = setTimeout(updateSecondsRemaining, 1000);
        }
      }

      // Function that ends the game
      function endGame() {
        // Cancel any outstanding timers.
        clearInterval(quaffleTimeoutID);
        clearInterval(snitchTimeoutID);
        clearInterval(secondsRemainingTimeoutID);
        clearInterval(gameTimeoutID);

        // Set the seconds remaining to zero
        secondsRemaining = 0;
        timer.innerHTML = secondsRemaining;

        // Hide the quaffle and snitch
        quaffle.style.visibility = "hidden";
        snitch.style.visibility = "hidden";
      }
    </script
  </body>
</html>
```