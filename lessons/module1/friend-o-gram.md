---
layout: default
---

# Friend-o-gram

## Goal

At the end of this activity, you will have built something similar to this:

![Friend-o-gram]()

## Overview

This activity will allow you to combine all the skills you have learned, HTML, CSS, and Visual Studio Code (aka VS Code).

## Instruction

### 1. Create a file

* First, on your desktop, right-click and select New Folder. Name it `friend-o-gram`.
* Open VS Code. In the toolbar at the top, under File, click New File. Save the file as `index.html` in your folder `friend-o-gram`.
* Copy and paste the following into your file in VS Code:

```
<!DOCTYPE html>
<html>
  <head></head>
  <body>
    Hello world!
  </body>
</html>
```
* Save the file and go to your desktop where you can see the folder `friend-o-gram`. Click into it and right-click on the `index.html` and open with Chrome (or whatever browser you have).
* You should see `Hello world!` on an otherwise blank screen.

### 2. Choose 6 photos

* Find and download 6 photos of you and/or friends and put all the files in the folder `friend-o-gram`.
  * Use Facebook or other online source to find the photos.
* Once the photos are in your folder, rename all the photos as `photo-1.jpg`, `photo-2.jpg`, etc.

### 3. Build HTML structure

* Our site is going to have 6 sections for the 6 photos. We are going to have 6 `div` elements that will have the photos as backgrounds.
* Put 6 `div` elements into your code.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head></head>
  <body>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
  </body>
</html>
```

* Label each div with 2 classes. 
  * The first class should be `photo` so that we can add the same CSS to all photos if we want.
  * The second class should be the same as the image name. So, photo-1 should have the class `photo-1` as so on. This allows us to add CSS to individual `div`s without affecting the other `div`s.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head></head>
  <body>
    <div class="photo photo-1"></div>
    <div class="photo photo-2"></div>
    <div class="photo photo-3"></div>
    <div class="photo photo-4"></div>
    <div class="photo photo-5"></div>
    <div class="photo photo-6"></div>
  </body>
</html>
```

### 4. Add CSS

* In the `head` section of your file, include `style` tags

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      
    </style>
  </head>
  ...
</html>
```