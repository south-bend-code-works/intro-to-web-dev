---
layout: default
---

# Friend-o-gram

## Goal

Our goal for this project is to build a sweet, web-based version of our favorite social media platform for sharing photos with our friends "on the line"! See if you can guess which one we are talking about based on the title of this project. 

At the end of this activity, you will have built something similar to this:

![best example]({{ site.baseurl }}/assets/img/module1/fog_best_example.png)

## Overview

This activity will allow you to combine all the skills you have learned, HTML, CSS, and Visual Studio Code (VS Code).

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
* Save the file and go to your desktop where you can see the folder `friend-o-gram`. Click into it and right-click on the `index.html` and open with Google Chrome.
* You should see `Hello world!` on an otherwise blank screen.

### 2. Choose 6 photos

* Find and download 6 photos of you and/or friends, and/or sweet memes, and/or pictures of things you like and put all the files in the folder `friend-o-gram`.
  * Use Facebook, Google, or other online source to find the photos.
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

* Label each div with a class and an ID. 
  * The class should be `photo` so that we can add the same CSS to all photos if we want. A class can be used on multiple elements, just like there are multiple students in this class.
  * The id should be unique to each photo, like your student ID is to you. So, the first photo should have the class `photo-1` as so on. This allows us to add CSS to individual `div`s without affecting the other `div`s.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head></head>
  <body>
    <div class="photo" id="photo-1"></div>
    <div class="photo" id="photo-2"></div>
    <div class="photo" id="photo-3"></div>
    <div class="photo" id="photo-4"></div>
    <div class="photo" id="photo-5"></div>
    <div class="photo" id="photo-6"></div>
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

      /* This is how you make a comment in CSS. */
      /* Anything inside the slash and asterisk will be ignored and is helpful for notes. */

    </style>
  </head>
  ...
</html>
```

* Make the body have 3 columns by using `grid`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        display: grid; /* This make the body a grid */
        grid-template-columns: auto auto auto; /* This tells the body element to split into 3 equal columns */
      }
    </style>
  </head>
  ...
</html>
```

* If you refresh and look at your site, you should still see nothing. However, the `body` has been divided into 3 equal columns. Since there are 6 `div` tags inside of `body`, this makes `body` a 3 by 2 grid of `div`s.

### 5. Add photos

* Currently, there are 6 `div`s in our `body` that have no height and no background images.
* The first step is to add height to our `div`s so that they aren't flat.
* In the CSS, grab all the `div`s using the selector `.photo` since all of the `div`s have that class. The period `.` before the word `photo` signals to CSS that it is the name of a class.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        display: grid;
        grid-template-columns: auto auto auto;
      }
      .photo {

      }
    </style>
  </head>
  ...
</html>
```

* Then, make all the `div`s have a height of `250px`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        display: grid;
        grid-template-columns: auto auto auto;
      }
      .photo {
        height: 250px;
      }
    </style>
  </head>
  ...
</html>
```

* Now that the `div`s have height, add the photos as background images.
* Using the CSS property `background-image`, link to the photos you saved earlier.


<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        display: grid;
        grid-template-columns: auto auto auto;
      }
      .photo {
        height: 250px;
      }
      #photo-1 {
        background-image: url('photo-1.jpg');
      }
      #photo-2 {
        background-image: url('photo-2.jpg');
      }
      #photo-3 {
        background-image: url('photo-3.jpg');
      }
      #photo-4 {
        background-image: url('photo-4.jpg');
      }
      #photo-5 {
        background-image: url('photo-5.jpg');
      }
      #photo-6 {
        background-image: url('photo-6.jpg');
      }
    </style>
  </head>
  ...
</html>
```

### 6. Resize photos

* If you refresh the page you have been working on, you should see 6 different images. However, they may not look like you expected. They may seem really 'zoomed in'.
* To fix this, we go back into the `.photo` selector in the CSS in order to change how the background looks.
* Add the `background-size` property to the `.photo` selector with the value `cover`


<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        display: grid;
        grid-template-columns: auto auto auto;
      }
      .photo {
        height: 250px;
        background-size: cover;
      }
      ...
    </style>
  </head>
  ...
</html>
```

* That likely makes it look some better but the photos are still likely not centered.
* Center the images by adding the property `background-position` with value `50% 50%`
  * This tells the background images to be centered both vertically and horizontally.


<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        display: grid;
        grid-template-columns: auto auto auto;
      }
      .photo {
        height: 250px;
        background-size: cover;
        background-position: 50% 50%;
      }
      ...
    </style>
  </head>
  ...
</html>
```

### 7. Cleaning up

* Some of the photos might not look their best being centered vertically and horizontally with a height of 200px.

![bad example]({{ site.baseurl }}/assets/img/module1/fog_bad_example.png)

* A lot of the photos don't seem tall enough to fit the parts of the picture that I want so I will increase the height to 400px.

![better example]({{ site.baseurl }}/assets/img/module1/fog_better_example.png)

* Better. However, I want photo 1 to be shifted lower. 
* So, instead of `background-position` being `50% 50%` for that photo, I'll use the same selector I used to set the background-image (`#photo-1`) to change just that photo's `background-position`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        display: grid; /* This make the body a grid */
        grid-template-columns: auto auto auto; /* This tells the body element to split into 3 equal columns */
      }
      .photo {
        height: 400px;
        background-size: cover;
        background-position: 50% 50%;
      }
      #photo-1 {
        background-image: url('photo-1.jpg');
        background-position: 50% 0%;
      }
      ...
    </style>
  </head>
  ...
</html>
```

* This results in:

![best example]({{ site.baseurl }}/assets/img/module1/fog_best_example.png)

* Cool! All the photos are where I want them to be.
* For your project, you will have to adjust individual photos to make things look good.
* Play around with different CSS properties (`background-size`, `background-position`, etc.) to gain an understanding of what they mean and how to use them.

## Conclusion

If you were able to see all photos and they look like you want them to, your knowledge of HTML and CSS is ready for our in-class session! Here is all the code from the example above:

```
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        display: grid;
        grid-template-columns: auto auto auto;
      }
      .photo {
        height: 400px;
        background-size: cover;
        background-position: 50% 50%;
      }
      #photo-1 {
        background-image: url('photo-1.jpg');
        background-position: 50% 0%;
      }
      #photo-2 {
        background-image: url('photo-2.jpg');
      }
      #photo-3 {
        background-image: url('photo-3.jpg');
      }
      #photo-4 {
        background-image: url('photo-4.jpg');
      }
      #photo-5 {
        background-image: url('photo-5.jpg');
      }
      #photo-6 {
        background-image: url('photo-6.jpg');
      }
    </style>
  </head>
  <body>
    <div class="photo" id="photo-1"></div>
    <div class="photo" id="photo-2"></div>
    <div class="photo" id="photo-3"></div>
    <div class="photo" id="photo-4"></div>
    <div class="photo" id="photo-5"></div>
    <div class="photo" id="photo-6"></div>
  </body>
</html>
```

## Bonus Mission 
If you'd like to spice up your friend-o-gram a bit, consider adding some of the following: 
* Background color to the webpage
* A fun logo at the top of the page 

Keep in mind that while there are no grades for this program, your projects will speak to the work you can do should you choose to use them as a part of your resume. 


