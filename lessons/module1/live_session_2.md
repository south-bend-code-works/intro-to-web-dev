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

## Zoom Link

TBD

## Quidditch 2.0 Instructions
In the second half of this live session you will break into small groups and individually enhance Quidditch 1.0 in the following ways:

### Features for 2.0:

1. Add the Golden Snitch.
    * Clicking the golden snitch earns 150 points AND ends the game.
    * The Snitch should be smaller than the actual image size, 32x32 px.  Use CSS to accomplish this.
    * The Snitch should be faster than the quaffle.
    * Hint: This will need a function similar to moveQuaffle().

2. Add a time limit to the game
    * Automatically End the Game after 15 seconds.
    * Show the time remaining in the game on the screen.
    * Hint: You should create a new function called updateTimer() that uses setTimeout() to call itself every second and update the time remaining in your HTML.

3. Add a background soundtrack to the game
    * Use the HTML5 Audio Tag
    * Download the background audio track here (or use your own!):
        * link to this file.

Your final game should look like this:
![](image here)
