---
layout: default
---

# Overview 

## Agenda
1. Review Arrays
2. Review Objects
3. Review and Enhance our random card selector
4. Upload our site to github

## Zoom Links

### Section 1 (10am to 12pm)
<https://notredame.zoom.us/j/96545079849?pwd=K3psL1J4Q3FUNmxCbmpSa0pTbm9ndz09>

**Meeting ID: 965 4507 9849**

**Passcode: 835805**

#### Section 1 Recording
<iframe src="https://notredame.hosted.panopto.com/Panopto/Pages/Embed.aspx?id=3e79ec52-8c63-4773-80a9-acad012a5e80&autoplay=false&offerviewer=true&showtitle=true&showbrand=false&start=0&interactivity=all" height="405" width="720" style="border: 1px solid #464646;" allowfullscreen allow="autoplay"></iframe>
### Section 2 (1pm to 3pm) 
<https://notredame.zoom.us/j/99670056329?pwd=OXRmSFNERU45Vi9ndkpJNUpGTFU1QT09>

**Meeting ID: 996 7005 6329**

**Passcode: 781595**

#### Section 2 Recording
<iframe src="https://notredame.hosted.panopto.com/Panopto/Pages/Embed.aspx?id=be0858c4-c2f3-46cf-8b71-acad015ac418&autoplay=false&offerviewer=true&showtitle=true&showbrand=false&start=0&interactivity=all" height="405" width="720" style="border: 1px solid #464646;" allowfullscreen allow="autoplay"></iframe>

### Section 3 (4pm to 6pm) 
<https://notredame.zoom.us/j/92241686868?pwd=aHBiTmdOM25Eak52UEtOQU5XeDJvZz09>

**Meeting ID: 922 4168 6868**

**Passcode: 122449**

#### Section 3 Recording
<iframe src="https://notredame.hosted.panopto.com/Panopto/Pages/Embed.aspx?id=e56f5c81-f405-487b-93e8-acad0185666b&autoplay=false&offerviewer=true&showtitle=true&showbrand=false&start=0&interactivity=all" height="405" width="720" style="border: 1px solid #464646;" allowfullscreen allow="autoplay"></iframe>


## Solution to Super Bonus

```
<!DOCTYPE html>
<html>

  <head>
    <style>
      #cards-holder {
        display: grid;
        grid-template-columns: repeat(4, 150px);
        column-gap: 16px;
      }
      .card {
        height: 170px;
        border: thick solid black;
        border-radius: 16px;
        display: grid;
        align-items: center;
        justify-items: center;
      }
    </style>
  </head>

  <body>

    <p>Pick the card you believe will be randomly selected.</p>
    <div id="cards-holder">

    </div>

    <h2>The selected card is <span id="selected-card"></span></h2>

    <h1>And our random card is:</h1>
    <h2 id="display"></h2>
    <button onclick="selectRandomCard()">Pick a random card</button>

  </body>

  <script>
    var deck = []
    var selectedCard = null

    var cardsHolderEle = document.getElementById("cards-holder")
    var selectedCardEle = document.getElementById("selected-card")
    var displayEle = document.getElementById("display")

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

    var askUserForAnotherRound = () => {
      var userWantsAnotherRound = confirm("Press OK for another round.")
      if (userWantsAnotherRound) {
        startRound()
      }
    }

    var selectRandomCard = () => {
      if (selectedCard === null) {
        alert("Select card first!")
      }
      else {
        var rand = Math.random()
        var larger = rand * 3
        var randomIndex = Math.round(larger)

        var randomCard = deck[randomIndex]

        var displayString = randomCard.value + " of " + randomCard.suit

        displayEle.innerHTML = displayString

        var selectedCardIsCorrectValue = randomCard.value === selectedCard.value
        var selectedCardIsCorrectSuit = randomCard.suit === selectedCard.suit

        if (selectedCardIsCorrectValue && selectedCardIsCorrectSuit) {
          alert("You guessed correctly!")
        } else {
          alert("Sorry. Wrong guess.")
        }

        setTimeout(askUserForAnotherRound, 3000)
      }
    }

    var selectCard = (card) => {
      selectedCard = card
      selectedCardEle.innerHTML = card.value + " of " + card.suit
    }

    var displayCard = (card) => {

      var cardEle = document.createElement("div")
      cardEle.className = "card"
      cardEle.innerHTML = card.value + " of " + card.suit
      cardEle.onclick = () => {
        selectCard(card)
      }

      cardsHolderEle.appendChild(cardEle)
    }

    var displayCards = () => {
      cardsHolderEle.innerHTML = ""

      displayCard(twoOfSpades)
      displayCard(fourOfClubs)
      displayCard(sevenOfDiamonds)
      displayCard(nineOfHearts)
    }

    var buildDeck = () => {
      deck = []
      deck.push(twoOfSpades)
      deck.push(fourOfClubs)
      deck.push(sevenOfDiamonds)
      deck.push(nineOfHearts)
    }

    var startRound = () => {
      displayCards()

      selectedCardEle.innerHTML = ""
      displayEle.innerHTML = ""
      selectedCard = null
    }

    buildDeck()
    startRound()

  </script>

</html>
 

```