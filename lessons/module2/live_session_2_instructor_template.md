<!--
Agenda:
0. House Keeping: Cover any issues / concerns for the course.
  - while and for loops
  - build deck
  - sort / shuffle
  - WAR

0.25 Start with analogies
  - Real world while loop
    - While I still have homework, I will continue to do homework
    - Restaurant closing
    - Swearing in front of kids
  - Real world for loop
    - For every tomato, cut the tomato

0.5 While loops
  - Just touch on a few while loop examples

----
  var counter = 0

    var num1 = 0
    var num2 = 1

    while (counter <= 5) {
      var previousNum2 = num2
      num2 += num1
      num1 = previousNum2

      counter += 1
    }

    console.log(num2)
----
----
    var num1 = 0
    var num2 = 1

    while (num2 <= 1000) {
      var currentNum2 = num2
      num2 = num1+num2
      num1 = currentNum2
    }

    console.log(num1)
----
  - explain that these are much less common than for loops

1. For Loops
  - examples of normal loops
    - console.log to demonstrate
    - adding things together
    - add a number to each
    - split a string and add "a" to every other letter
    - example where you use anonymous and named functions
  - example of loops within loops
    - start with console.log examples
    - create one long string from 2 arrays of strings
      - using both anonymous and named functions

2. New deck
  - build buildDeck function
  - both with anonymous functions and named functions

----
    var suits = ["hearts", "spades", "diamonds", "clubs"]
    var values = [1,2,3,4,5,6,7,8,9,10,11,12,13]

    var deck = []

    suits.forEach((suitVal) => {
      values.forEach((valueVal) => {

        var card = {
          value: valueVal,
          suit: suitVal,
        }

        deck.push(card)

      })
    })
----

3. Shuffle
  var twoOfSpades = {
      suit: "spades",
      value: 2,
    }

    var fiveOfDiamonds = {
      suit: "diamonds",
      value: 5,
    }

    var threeOfHearts = {
      suit: "hearts",
      value: 3,
    }

    var arr = [twoOfSpades, fiveOfDiamonds, threeOfHearts]


    var sortFunction = (card1, card2) => {
      var rand = Math.random()
      if (rand > .5) {
        return 1
      } else {
        return -1
      }
    }


    arr.sort(sortFunction)

    console.log(arr)

3. WAR
  - If time allows it, allow students to try and build WAR
  - Walk thru how to build war

-->

<!DOCTYPE html>

<html>

  <head>
    <style>
      .play-area {
        display: grid;
        grid-template-columns: 1fr 1fr;
      }
      .card {
        height: 180px;
        width: 100px;
        border: thick solid black;
        border-radius: 16px;
        display: grid;
        align-items: center;
        justify-items: center;
      }
    </style>
  </head>

  <body>

    <div class="play-area">

      <div class="player">
        <h1>Player 1</h1>
        <h2>Cards remaining: <span id="player-1-total">26</span></h2>
        <div id="player-1-battle-card" class="card"></div>
      </div>

      <div class="player">
        <h1>Player 2</h1>
        <h2>Cards remaining: <span id="player-2-total">26</span></h2>
        <div id="player-2-battle-card" class="card"></div>
      </div>

      <h1>Active cards: <span id="active-cards">0</span></h1>

      <button onclick="startRound()">Start Round</button>
    </div>

  </body>

  <script>
    var values = [1,2,3,4,5,6,7,8,9,10,11,12,13]
    var suits = ["hearts", "spades", "diamonds", "clubs"]

    var p1TotalEle = document.getElementById("player-1-total")
    var p2TotalEle = document.getElementById("player-2-total")
    var p1BattleCardEle = document.getElementById("player-1-battle-card")
    var p2BattleCardEle = document.getElementById("player-2-battle-card")
    var activeCardsEle = document.getElementById("active-cards")

    var deck = []

    var p1Deck = []
    var p2Deck = []

    var activeCards = []

    var p1BattleCard = null
    var p2BattleCard = null

    var buildDeck = () => {

      var newDeck = []

      values.forEach((value) => {
        suits.forEach((suit) => {
          var card = {
            value: value,
            suit: suit,
          }
          newDeck.push(card)
        })
      })
      
      return newDeck
    }

    var shuffleDeck = () => {
      deck.sort((a, b) => {
        var rand = Math.random()
        var result
        if (rand < .5) {
          result = -1
        } else {
          result = 1
        }
        return result
      })
    }

    var dealCards = () => {
      p1Deck = []
      p2Deck = []

      var dealToP1 = true

      while (deck.length > 0) {
        var topCard = deck.shift()
        if (dealToP1) {
          p1Deck.push(topCard)
        } else {
          p2Deck.push(topCard)
        }
        dealToP1 = !dealToP1
      }
    }

    var checkForWinner = () => {
      var p1HasLost = p1Deck.length === 0
      var p2HasLost = p2Deck.length === 0

      return p1HasLost || p2HasLost
    }

    var updateHtml = () => {
      p1TotalEle.innerHTML = p1Deck.length
      p2TotalEle.innerHTML = p2Deck.length
      p1BattleCardEle.innerHTML = p1BattleCard.value + " of " + p1BattleCard.suit
      p2BattleCardEle.innerHTML = p2BattleCard.value + " of " + p2BattleCard.suit
      activeCardsEle.innerHTML = activeCards.length
    }

    var decideRound = () => {
      if (p1BattleCard.value === p2BattleCard.value) {
        playCards(true)
      } else if (p1BattleCard.value > p2BattleCard.value) {
        p1Deck = p1Deck.concat(activeCards)
      } else {
        p2Deck = p2Deck.concat(activeCards)
      }
      updateHtml()
    }

    var endGame = () => {
      if (p1Deck.length === 0) {
        alert("player 2 won!")
      } else {
        alert("player 1 won!")
      }
      alert("a new game is about to start.")
      startGame()
    }

    var playCards = (isWar) => {
      var someoneHasWon = checkForWinner()
      if (someoneHasWon) {
        endGame()
      } 
      else if (isWar) {
        activeCards.push(p1Deck.shift())
        activeCards.push(p2Deck.shift())
        playCards(false)
      } 
      else {
        var p1TopCard = p1Deck.shift()
        var p2TopCard = p2Deck.shift()

        p1BattleCard = p1TopCard
        p2BattleCard = p2TopCard

        activeCards.push(p1TopCard)
        activeCards.push(p2TopCard)
        
        decideRound()
      }
    }

    var startRound = () => {
      activeCards = []
      playCards(false)
    }

    var startGame = () => {
      deck = buildDeck()
      shuffleDeck()
      dealCards()
    }

    startGame()



  </script>

</html>
