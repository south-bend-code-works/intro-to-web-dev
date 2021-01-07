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
