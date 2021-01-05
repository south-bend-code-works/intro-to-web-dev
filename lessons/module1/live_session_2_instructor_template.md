<!--

Agenda:

0. House Keeping: Cover any issues / concerns for the course.
    
1. Using functions and basic logic in JavaScript
2. Learn the Document Object Model (DOM) and combine HTML, CSS, and JavaScript to build interactive websites. 
3. Quidditch Cup 2.0 in Small Groups
3. Hosting you Quidditch Cup 2.0 on GitHub and Github Sites.
4. (last 5 minutes)
    - Review Final Project Part 2 
    - Talk about the upcoming lab and it's format
-->


<!--
 _  _   _  _____  ___    ___    ___    _____  _____  _  _   _  ___       _____  _____  _   _  _____  ___    ___    ___    _  ___   _____ 
(_)( ) ( )(_   _)(  _`\ (  _`\ |  _`\ (  _  )(_   _)(_)( ) ( )(  _`\    (___  )(  _  )( ) ( )(  _  )(  _`\ (  _`\ |  _`\ (_)(  _`\(_   _)
| || `\| |  | |  | (_(_)| ( (_)| (_) )| (_) |  | |  | || `\| || ( (_)       | || (_) || | | || (_) || (_(_)| ( (_)| (_) )| || |_) ) | |  
| || , ` |  | |  |  _)_ | |___ | ,  / |  _  |  | |  | || , ` || |___     _  | ||  _  || | | ||  _  |`\__ \ | |  _ | ,  / | || ,__/' | |  
| || |`\ |  | |  | (_( )| (_, )| |\ \ | | | |  | |  | || |`\ || (_, )   ( )_| || | | || \_/ || | | |( )_) || (_( )| |\ \ | || |     | |  
(_)(_) (_)  (_)  (____/'(____/'(_) (_)(_) (_)  (_)  (_)(_) (_)(____/'   `\___/'(_) (_)`\___/'(_) (_)`\____)(____/'(_) (_)(_)(_)     (_)  
                                                                                                                                         
                                                                                                                                         
Goals:
- Get them to use JavaScript on some site they have locally
- show an alert to explain that JS is the "interactive" part
- interact with DOM by editing some element
- show an onClick event that triggers an alert via a <button>
-->

<!-- Step 1: An Alert -->
<!DOCTYPE html>
<html>
    <body>
        <p>Hello, World!</p>
        <script>
            alert("I am an alert!");
        </script>
    </body>
</html>

<!-- Step 2: An Alert via a button click -->
<!DOCTYPE html>
<html>
    <body>
        <button onclick="sayHello()">Hello, World!</button>
        <script>
            function sayHello() {
                alert("I can say hello!")
            }
        </script>
    </body>
</html>

<!-- Step 3: Use DOM events -->
<!DOCTYPE html>
<html>
    <body>
        <button id="btn">Hello, World!</button>
        <script>
            var btn = document.getElementById("btn")

            function sayHello() {
                alert("I say hello when you click on the btn")
            }

            btn.onclick = sayHello
        </script>
    </body>
</html>

<!-- Step 4: Edit the DOM -->
<!DOCTYPE html>
<html>
    <body>
        <button id="btn">Hello, World!</button>
        <script>
            var btn = document.getElementById("btn")

            function sayHello() {
                btn.innerText = "Changing the DOM."
            }

            btn.onclick = sayHello
        </script>
    </body>
</html>

<!--
 _____  _   _  _  ___    ___    _  _____  ___    _   _       _      __   
(  _  )( ) ( )(_)(  _`\ (  _`\ (_)(_   _)(  _`\ ( ) ( )    /' )   /' _`\ 
| ( ) || | | || || | ) || | ) || |  | |  | ( (_)| |_| |   (_, |   | ( ) |
| | | || | | || || | | )| | | )| |  | |  | |  _ |  _  |     | |   | | | |
| (('\|| (_) || || |_) || |_) || |  | |  | (_( )| | | |     | | _ | (_) |
(___\_)(_____)(_)(____/'(____/'(_)  (_)  (____/'(_) (_)     (_)(_)`\___/'
                                                                         
Walk through the code and explain how JavaScript is used to for DOM events and directly editing the DOM in version quidditch 1.0


-->

<!--
 _____  _   _  _  ___    ___    _  _____  ___    _   _       __        __   
(  _  )( ) ( )(_)(  _`\ (  _`\ (_)(_   _)(  _`\ ( ) ( )    /'__`\    /' _`\ 
| ( ) || | | || || | ) || | ) || |  | |  | ( (_)| |_| |   (_)  ) )   | ( ) |
| | | || | | || || | | )| | | )| |  | |  | |  _ |  _  |      /' /    | | | |
| (('\|| (_) || || |_) || |_) || |  | |  | (_( )| | | |    /' /( ) _ | (_) |
(___\_)(_____)(_)(____/'(____/'(_)  (_)  (____/'(_) (_)   (_____/'(_)`\___/'

* Note: They should all have the completed solution for Quidditch 1.0 as the starting point for 2.0

* Explain the objective of Quidditch 2.0
* Breakout into small groups of 3-4. 
* Individual Groups should help each other implement Quidditch 2.0.

* WITH 15 MINUTES OF CLASS LEFT
* Close the breakout rooms
* Share the final solution via a github gist in the zoom chat.
* Walk the class through the solution to Quidditch 2.0


Extend our Quidditch Game:
1. Add the Golden Snitch.
    * Clicking the golden snitch earns 150 points AND ends the game.
    * The Snitch should be smaller than the actual image size, 32x32.  Use CSS to accomplish this.
    * The Snitch should be faster than the quaffle.

2. Add a time limit to the game
    * Automatically End the Game after 15 seconds.
    * Show the time remaining in the game on the screen.

3. Add a background soundtrack to the game
    * Use the HTML5 Audio Tag


Quiddtich 2.0 Solution Below
-->

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
