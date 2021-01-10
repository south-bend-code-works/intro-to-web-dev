<!--

0. Overview

- General questions / concerns for the course

- Recap on the previous week
  - Great job!
  - Recap the previously learned concepts
    - HTML - structure and content
    - CSS - styling and design
    - JS - allows us to program things like games and functionality
  - Here is how the new things build onto those

- Discuss agenda for the live session

1. Arrays

- Use prework as a template to review the array functionality
  - Initializing an array
  - Add to an array manually
  - Pushing to an array
  - Getting from an array
  - Other array functionalities
    - length
    - concatenation
      var arr1 = [1,2,3]
      var arr2 = [3,4,5]

      var longArr1 = arr1.concat(arr2)

      // value of longArr1 is [1,2,3,3,4,5]

      var longArr2 = arr2.concat(arr1)

      // value of longArr2 is [3,4,5,1,2,3]
    - includes
    - indexOf

2. Objects

- Use prework as a template to review the object functionality
  - Initializing an object
  - Very slowly talking thru the construction and format of an object
    - key vs values
  - Discuss how we use objects to create concepts in JS (like people or cards or anything)
  - Getting a value from an object
  - Adding to an object
  - Removing from an object
  - Editing an existing property in an object

3. Build from scratch the random card selector, going very slowly
  - Talk about random and round

4. Provide time for the students to try out the super bonus mission on their own in groups
  - Bring students back in with 30 minutes to go over super bonus mission solution
  - I would say copy and paste the whole solution (which is below) and then walk thru the code after demoing the game
  - Try to have enough time to push code to github as a class

5. Close out class
  - Review what needs to be done before next live session
  - Close class but offer the option to stick around with questions 
-->

<!-- Super bonus solution -->

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

    <h2>The chosen card is <span id="chosen-card"></span></h2>

    <h1>And our random card is:</h1>
    <h2 id="display">No card picked yet</h2>
    <button onclick="selectRandomCard()">Pick a random card</button>

  </body>

  <script>
    var deck = []
    var selectedCard = false

    var cardsHolderEle = document.getElementById("cards-holder")
    var selectedCardEle = document.getElementById("chosen-card")
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
      if (!selectedCard) {
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
      buildDeck()
      displayCards()
      selectedCardEle.innerHTML = ""
      displayEle.innerHTML = ""
      selectedCard = false
    }

    startRound()

  </script>

</html>
