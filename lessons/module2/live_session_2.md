---
layout: default
---

# Overview 

## Agenda
1. Review Loops
2. Walk through our deck of cards solution
3. Create 2 decks of cards and play a simple game of WAR (high card wins)
4. Upload our deck of cards and WAR game to git and host it on github pages.

## Zoom Links

### Section 1 (10am to 12pm)
<https://notredame.zoom.us/j/96545079849?pwd=K3psL1J4Q3FUNmxCbmpSa0pTbm9ndz09>

**Meeting ID: 965 4507 9849**

**Passcode: 835805**

#### Section 1 Recording
<iframe src="https://notredame.hosted.panopto.com/Panopto/Pages/Embed.aspx?id=cd4e2c5d-81e1-4cfc-9bed-acaf01199269&autoplay=false&offerviewer=true&showtitle=true&showbrand=false&start=0&interactivity=all" height="405" width="720" style="border: 1px solid #464646;" allowfullscreen allow="autoplay"></iframe>

### Section 2 (1pm to 3pm) 
<https://notredame.zoom.us/j/99670056329?pwd=OXRmSFNERU45Vi9ndkpJNUpGTFU1QT09>

**Meeting ID: 996 7005 6329**

**Passcode: 781595**

#### Section 2 Recording
<iframe src="https://notredame.hosted.panopto.com/Panopto/Pages/Embed.aspx?id=4fd6d799-b677-4e81-b447-acaf0157b799&autoplay=false&offerviewer=true&showtitle=true&showbrand=false&start=0&interactivity=all" height="405" width="720" style="border: 1px solid #464646;" allowfullscreen allow="autoplay"></iframe>

### Section 3 (4pm to 6pm) 
<https://notredame.zoom.us/j/92241686868?pwd=aHBiTmdOM25Eak52UEtOQU5XeDJvZz09>

**Meeting ID: 922 4168 6868**

**Passcode: 122449**

#### Section 3 Recording
<iframe src="https://notredame.hosted.panopto.com/Panopto/Pages/Embed.aspx?id=cd859319-d012-484c-811d-acaf018961b0&autoplay=false&offerviewer=true&showtitle=true&showbrand=false&start=0&interactivity=all" height="405" width="720" style="border: 1px solid #464646;" allowfullscreen allow="autoplay"></iframe>

## Solution for WAR:

```
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
      } 
      else if (p1BattleCard.value > p2BattleCard.value) {
        p1Deck = p1Deck.concat(activeCards)
      } 
      else {
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
```