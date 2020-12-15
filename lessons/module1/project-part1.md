---
layout: default
---

# Project Part 1: Virtual Pet

## Goal

The goal for this project is to begin building a Virtual Pet. At the end of both parts of this project, you will have a Virtual Pet that is needs food, water, and exercise and responds to how well balanced these needs are being handled. At the end, you will have built a webpage that looks something like this:

![]({{ site.baseurl }}/assets/img/module1/vp-interactive-5.png)

## Overview

There are 2 parts to this project. The first part, which you will be doing now, is to build the structure and layout of the page, decorate with the colors and themes of your choosing, and assemble the assets (which just means images or photos) which will be used for this project.

## Steps

### Files

In order to start your page, you will need a new folder and a new file. Go to your desktop and create a new folder called `virtual-pet`. Then, open up VS Code and create a new file called index.html and save it inside of your `virtual-pet` folder.

As always, you need to start will the bare bones of a website which is this:

```
<!DOCTYPE html>
<html>
  <head></head>
  <body>
    Hello world!
  </body>
</html>
```

After copying and pasting that into the file, go to the folder `virtual-pet` on you desktop, open it, right-click on `index.html`, and choose to open in your browser. Confirm that you can see `Hello world!`. If so, you are ready to get started.

### Structure

Before starting a webpage, we should always be thinking about what we will need to include in that page. This allows us to formulate how we would like to set up our page and, therefore, our HTML.

Our Virtual Pet page will need 3 things:
1. A header where we can name our virtual pet and maybe have a description.
2. A stats and interaction area where we will be able to see how healthy and balanced our Virtual Pet is.
3. An area where we will display different pictures based on how healthy (or not ) our Virtual Pet is.

A good practice is to draw a general and simple design (aka mockup) of what we are trying to make. Here is mine:

![Virtual Pet Mockup]({{ site.baseurl }}/assets/img/module1/virtual_pet_mockup.png)

We can see from the mockup that the whole page is divided into 2 rows, **Header Area** and **Main Area**. Furthermore, **Main Area** is divided into 2 columns, **Image Area** and **Stats and Buttons Area**. Now that we have the general structure in mind, we can write HTML that matches it:

```
<!DOCTYPE html>
<html>
  <head></head>
  <body>
    <div class="header"></div>
    <div class="main">
      <div class="image-area"></div>
      <div class="interactive-area"></div>
    </div>
  </body>
</html>
```

You can see above that I added 4 `div`s to represent the 4 areas I mentioned above.

In order differentiate between the areas, I added **classes** to the `div`s with the short names `header`, `main`, `image-area`, and `interactive-area` (the area for button and stats). Naming the `div`s like this allows us to do 2 things:
1. The names remind us what the `div`'s purpose is.
2. We can use the `div`s' classes as selectors in our CSS.

You may also notice that the `header` `div` is empty while the `main` `div` has 2 other `div`s inside of it. The reason for this is because, looking at the mockup above, we are planning on splitting `main` into 2 columns while leaving `header` as just one column.

### The Animal

Next, we have to make a decision about what we want our Virtual Pet to be. It can be real, imaginary, a Pokemon, whatever you want. The only requirement is that you find images or gifs online of this creature for each of the following moods:
1. Neutral: not too happy but not too sad. Just a neutral image or gif for when the pet is just fine.
2. Tired: this image will show when the animal is struggling and about to pass out.
3. Passed out: an image for when one of the pet's stats has reached zero.
4. Upbeat: the pet is doing well! A fun little trot or walk to how happiness and healthiness.
5. Exuberant: for when the animal is just crushing life. Should be the happiest, most excited version of your pet.

Once you find all of your photos online, download them and put them into your `virtual-pet` folder. You should rename them to match their state. **Note: when renaming them, keep the file extension they were downloaded with. So, if you downloaded a gif, the last part of the name should be `.gif`. Don't change that part, just the part in front of it.**

I will choose the Loch Ness Monster as my pet. Here is an example of my `neutral.gif`:

![]({{ site.baseurl }}/assets/img/module1/neutral.gif){: style="max-width:300px"}

I have also gone ahead and downloaded images or gifs for the other 4 states (`tired`, `passed-out`, `upbeat`, and `exuberant`) into my `virtual-pet` folder.

### The header

Now that we have decided on a creature and have our structure, we can start putting real content onto the page. Let's start with the `header`.

In our `header`, we want 2 things: a `pet-name` and a `description`. Let's go ahead and add appropriately classed `div`s into our HTML.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head></head>
  <body>
    <div class="header">
      <div class="pet-name"></div>
      <div class="description"></div>
    </div>
    <div class="main">
      <div class="image-area"></div>
      <div class="interactive-area"></div>
    </div>
  </body>
</html>
```

Now that we have the `div`s in place. Let's come up with a name and a description for our pet. I'll name mine `Big L` and use the description `He is big and not good at things.` Whatever you decide for a name and description, put that content in between the appropriate tags.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head></head>
  <body>
    <div class="header">
      <div class="pet-name">Big L</div>
      <div class="description">He is big and not good at things.</div>
    </div>
    <div class="main">
      <div class="image-area"></div>
      <div class="interactive-area"></div>
    </div>
  </body>
</html>
```

If you refresh your page that you opened earlier, it should look something like this: 

![]({{ site.baseurl }}/assets/img/module1/vp-header-1.png)

Well, it's there but it is not pretty. Let's add some CSS to spruce things up a bit. Let's start with adding `style` tag into the currently empty `head` tag:

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      
    </style>
  </head>
  <body>
    <div class="header">
      <div class="pet-name">Big L</div>
      <div class="description">He is big and not good at things.</div>
    </div>
    <div class="main">
      <div class="image-area"></div>
      <div class="interactive-area"></div>
    </div>
  </body>
</html>
```

First things first, that font has to go. Let's add a new font to the whole page by using the `body` selector (to select everything between the `body` tags) and using the property `font-family` to change the font to something new. [Here](https://www.w3schools.com/cssref/css_websafe_fonts.asp) is a list of fonts to use and examples on how to use them. I'm going to choose `'Courier New', Courier, monospace` as the font for my whole page.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        font-family: 'Courier New', Courier, monospace;
      }
    </style>
  </head>
  ...
</html>
```

After refreshing the page, I can see my font has changed. The font looks a little thin and hard to see, so I'll add `font-weight: bold` to my `body`'s CSS.

While that looks better, I wish my `pet-name` was larger than the description. So, I'll add `font-size: 32px` to a `.pet-name` selector in my CSS.

I'm liking the way this is starting to look, but I wish the words weren't so close to the edge of the screen. So, I'll add `padding: 32px` to the `header` and call it good enough for the header. (`padding` is used in CSS to basically put a cushion of space around it's contents. In my example, I put `32px`, or 32 pixels, of cusion around my `pet-name` and `description`.)

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        font-family: 'Courier New', Courier, monospace;
        font-weight: bold;
      }
      .header {
        padding: 32px;
      }
      .pet-name {
        font-size: 32px;
      }
    </style>
  </head>
  ...
</html>
```

![]({{ site.baseurl }}/assets/img/module1/vp-header-2.png)

### The main

Alright, so we have our header in place. Looking at the mockup, it looks like we go ahead and start developing our **Main Area**. In the code, our **Main Area** is the `div` classed as `main` and has 2 `div`s inside of it, `image-area` and `interactive-area`. From the mockup, we know we want to have **Main Area** split into 2 equal halves that are side-by-side. However, if I type a few words into the `divs`s `image-area` and `interactive-area`, this is what I get:

![]({{ site.baseurl }}/assets/img/module1/vp-main-1.png)

From the image, you can see the 2 `div`s are stacked on top of each other. This is the default for how `div`s interact and we need to change that with CSS. What we need to do is to tell `main` to make itself a grid where there are 2 columns that are side by side, just like in the mockup. I'll do that by adding CSS to the `main` `div`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        font-family: 'Courier New', Courier, monospace;
        font-weight: bold;
      }
      .header {
        padding: 32px;
      }
      .pet-name {
        font-size: 32px;
      }
      .main {
        display: grid; /* this tells `main` to be a grid*/
        /* this next line tells `main` that, since it is a grid now, to separate into 2 equal columns*/
        grid-template-columns: 1fr 1fr; 
      }
    </style>
  </head>
  ...
</html>
```

We can see below that it appears `main` has indeed been separated into 2 columns with `image-area` on the left and `interactive-area` on the right. I added color to the background so you could see the areas more clearly.

![]({{ site.baseurl }}/assets/img/module1/vp-main-2.png)

### Image area

Now that we have divided the `main` area into 2 columns (like in the mockup) we are able to start fleshing out each of the parts inside, the `image-area` and the `interactive-area`. Let's start with the `image-area`.

The `image-area`'s only job is to display a photo that matches the state of our Virtual Pet. The way we are going to do this is to add an `img` element into `image-area` with class `pet-image` and `src` set to our `neutral` image.

So, let's add that `img` element.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <body>
    <div class="header">
      <div class="pet-name">Big L</div>
      <div class="description">He is big and not good at things.</div>
    </div>
    <div class="main">
      <div class="image-area">
        <img class="pet-image" src='neutral.gif' />
      </div>
      <div class="interactive-area">I'm the interactive area</div>
    </div>
  </body>
</html>
```

The result of adding that line is the following:

![]({{ site.baseurl }}/assets/img/module1/vp-image-1.png)

So, your image may look very large or small compared to what you see above. However, as long as you see an image, you've done it right!

So, there is a good chance all of your photos that you have chosen for your pet are different sizes. We want to establish some consistency between the pictures. Using CSS, let's add sizing to our image. Let's make all of our images have the same height of `500px`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      ...
      .pet-image {
        height: 500px;
      }
      ...
    </style>
  </head>
  ...
</html>
```

Now, no matter what the dimensions of the photos actually are, the height will be `500px`. This may result in some of your photos being blurry and that's okay.

One issue you may run into is that if you have a very wide photo (a photo where the width is much larger than the height), by setting the `height` to `500px` may cause a picture to be wider than the half of the screen it's supposed to stay on. In order to prevent a photo from bleeding over into the other half of the screen, add `max-width: 100%;` to `pet-image`. This tells the `img` that its maximum width is as it's container (which is `image-area` which is half the screen). By adding this line to the CSS, if you do have a very wide image, that image will be distorted. That is fine. It is better that the image is distorted rather to have that image covering the `interactive-area` or not be seen at all.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      ...
      .pet-image {
        height: 500px;
        max-width: 100%;
      }
      ...
    </style>
  </head>
  ...
</html>
```

This previous changes results in the following:

![]({{ site.baseurl }}/assets/img/module1/vp-image-2.png)

Okay, so now we know that all of our images will be `500px` in height and won't overflow into the other half of the screen, let's make our `image-area` look a little nicer. I'm going to do 2 things: add space around the image to give it some breathing room and make sure that the image is centered inside of `image-area`.

In order to add space around the image, I will add `32px` worth of `padding` to `pet-image`.

While adding extra space was pretty simple, centering things in CSS tends to not be as easy as we wish. 

There are 2 ways of thinking about centering something in CSS: tell that element to center itself or to ask the element it is inside of (a.k.a. the parent element) to center all of its elements. Telling the parent element to center all of the items inside of it tends to be easier than telling the element to center itself, so I will take the easier route.

So, since `image-area` is the parent to `pet-image`, we need to add CSS to `image-area` so that it centers `pet-image`. We have seen `grid` used in our CSS several times already. `grid` has tons of cool features besides making columns, it can also center items! So, first we make `image-area` a `grid` by adding `display: grid`. Then, we tell it to center the items inside of it by also adding `justify-items: center`. This will horizontally align all items inside of this element which, in this case, is just `pet-image`.


<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      ...
      .image-area {
        background-color: #FFC292;
        display: grid;
        justify-items: center;
      }
      .pet-image {
        height: 500px;
        max-width: 100%;
        padding: 3rem;
      }
      ...
    </style>
  </head>
  ...
</html>
```

This results in the following:

![]({{ site.baseurl }}/assets/img/module1/vp-image-3.png)

Cool! That looks pretty good. Just to make sure I like it, I'll change the `src` of the `img` to see how my other pictures look.

I like what I see so I will continue on.

### Interactive area

The last thing we need to do to set up our page is to set up our buttons and stats in the `interactive-area`.

Before we start adding any HTML and CSS, let's plan ahead. I'll do this by going back to my mockup from earlier and adding details to the **Stats and Buttons Area**.

We know that we are going to need 3 stats and 3 buttons. So, we can just add these generally to the mockup to figure out approximately what it will look like:

![]({{ site.baseurl }}/assets/img/module1/virtual_pet_mockup_1.png)

So, the plan looks like I will have 3 rows, one for each activity. `(icon)` will be an image that represents the activity. `(stat)` is where the numerical value for the state of that acitivy will be shown. `(activity)` will be a button that can be pushed to perform that activity.

Based on what we have above, we are going to need 3 rows with each row holding 3 things. Let's write some HTML to represent what we need:

```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    <div class="header">
      <div class="pet-name">Big L</div>
      <div class="description">He is big and not good at things.</div>
    </div>
    <div class="main">
      <div class="image-area">
        <img class="pet-image" src="neutral.gif" />
      </div>
      <div class="interactive-area">

        <div class="activity-row">
          <img class="activity-icon" src="" />
          <div class="activity-stat"></div>
          <div class="activity-button"></div>
        </div>
        <div class="activity-row">
          <img class="activity-icon" src="" />
          <div class="activity-stat"></div>
          <div class="activity-button"></div>
        </div>
        <div class="activity-row">
          <img class="activity-icon" src="" />
          <div class="activity-stat"></div>
          <div class="activity-button"></div>
        </div>
        
      </div>
    </div>
  </body>
</html>
```

Looking at the code above, there are a few things to notice:
- There are 3 `div`s with the class `activity-row`. This represents the 3 rows in the mockup.
- Within each `activity-row` are 3 elements:
  1. An image (`activity-icon`) where the activity's icon will go
  2. A `div` with class `activity-stat` where the acivity's stat will be shown
  3. A `div` with class `activity-button` where will we make a button so that we can interact with that activity

You can see in the HTML that the `activity-icon`s don't have anything in their `src` attribute. Let's go ahead and find icons to represent each of our activities: food, water, and exercise. After find those icons, download them into your `virtual-pet` folder and name them appropriately. Then, change the `src` attribute in the `img`s to match the images you have downloaded.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <body>
    ...
    <div class="main">
      ...
      <div class="interactive-area">

        <div class="activity-row">
          <img class="activity-icon" src="food.png" />
          <div class="activity-stat"></div>
          <div class="activity-button"></div>
        </div>
        <div class="activity-row">
          <img class="activity-icon" src="water.png" />
          <div class="activity-stat"></div>
          <div class="activity-button"></div>
        </div>
        <div class="activity-row">
          <img class="activity-icon" src="exercise.png" />
          <div class="activity-stat"></div>
          <div class="activity-button"></div>
        </div>

      </div>
    </div>
  </body>
</html>
```

This is what my page looked like after downloading and adding the pictures:

![]({{ site.baseurl }}/assets/img/module1/vp-interactive-1.png)

Oh my. Well, they are there but they seem a little too large...

I'm going to make all of my `activity-icon`s the same size. I'm going to set both the `width` and `height` to `40px`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      ...
      .activity-icon {
        height: 40px;
        height: 40px;
      }
    </style>
  </head>
  ...
</html>
```

Okay, much better.

Now that icons are in a good spot, let's put numbers in the `activity-stat` `div`s in order to see what it will look like.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <body>
    ...
    <div class="main">
      ...
      <div class="interactive-area">

        <div class="activity-row">
          <img class="activity-icon" src="food.png" />
          <div class="activity-stat">100</div>
          <div class="activity-button"></div>
        </div>
        <div class="activity-row">
          <img class="activity-icon" src="water.png" />
          <div class="activity-stat">50</div>
          <div class="activity-button"></div>
        </div>
        <div class="activity-row">
          <img class="activity-icon" src="exercise.png" />
          <div class="activity-stat">5</div>
          <div class="activity-button"></div>
        </div>

      </div>
    </div>
  </body>
</html>
```

This results in:

![]({{ site.baseurl }}/assets/img/module1/vp-interactive-2.png)

At this point, I am realizing I need to make my `activity-row`s have 3 columns for the icon, stat, and button. The easiest way to do this is to make the `activity-row`s into `grid`s with 3 columns.

I also don't like how all of the `activity-row`s are all crammed together into the corner. So, I center them by telling their parent element (`interactive-area`) to center them.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      ...
      .interactive-area {
        background-color: #00BEBD;
        display: grid;
        align-items: center; /* This centers all elements inside of this element vertically */
        justify-items: center; /* This centers all elements inside of this element horizontally */
      }
      .activity-row {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr; /* This creates 3 columns of equal length */
      }
      ...
    </style>
  </head>
  ...
</html>
```

Adding this CSS results in:

![]({{ site.baseurl }}/assets/img/module1/vp-interactive-3.png)

Okay, so, things are looking better but we still can't really see a button. The `div`s for the buttons are there (`activity-button`), but there is no content in the buttons (they are empty `div`s) and there is no CSS decorating the buttons. Let's change that! Let's add action words to the buttons that match the activity. I'm going to add the words `Eat fish`, `Drink water`, and `Exercise` to the cooresponding buttons.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  ...
  <body>
    ...
    <div class="main">
      ...
      <div class="interactive-area">

        <div class="activity-row">
          <img class="activity-icon" src="food.png" />
          <div class="activity-stat">100</div>
          <div class="activity-button">Eat fish</div>
        </div>
        <div class="activity-row">
          <img class="activity-icon" src="water.png" />
          <div class="activity-stat">50</div>
          <div class="activity-button">Drink water</div>
        </div>
        <div class="activity-row">
          <img class="activity-icon" src="exercise.png" />
          <div class="activity-stat">5</div>
          <div class="activity-button">Exercise</div>
        </div>

      </div>
    </div>
  </body>
</html>
```

Okay, I can now see where my buttons will be but they just look like words, not buttons. So, in order to make them look more button-like, I will add the following:
- `background-color: #B27499`
  - `#B27499` is hexcode which is a way to choose color in CSS
- `border-radius: 8px`
- `box-shadow: 0 0 5px 0 grey`
  - the first 2 numbers in `box-shadow` values is how many pixels down and right we want the shadow compared to the element
  - the next number is how many pixels spread out we want the shadow
  - the next number is how many pixels larger we want the shadow to start out as
  - the last value is the color of the shadow
- `color: white`
  - `color` refers to font-color
- `cursor: pointer`
  - this controls what the mouse looks like when it is over the element

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      ...
      .activity-button {
        background-color: #B27499;
        border-radius: 8px;
        box-shadow: 0 0 5px 0 grey;
        color: white;
        cursor: pointer;
      }
      ...
    </style>
  </head>
  ...
</html>
```

This gives us:

![]({{ site.baseurl }}/assets/img/module1/vp-interactive-4.png)

Well, at least we have buttons. Not good buttons, but they definitely exist.

Realistically, we have all of the elements we need. However, it seems like it could use a little cleaning up. Here are the following items I would like to make better before calling this good:
- All `activity-icon`s should be aligned to the left
- All `activity-stat`s should be aligned in the center
- All `activity-button`s should be aligned to the right
- All the elements in an `activity-row` should be center-aligned vertically
  - Currently, all aligned to the top
- The buttons should have padding to the left and right of the word inside
- The buttons text should be centered within the button

Let's start with aligning the elements within `activity-row`s. First off, the `activity-row`s are all at different widths. They are only as wide as they are due to the width of the button. Because we are using `grid-template-columns: 1fr 1fr 1fr` in our `activity-row`s, all of the columns in an `activity-row` are going to be the same width. So, since some of the buttons are wider (due to more letters inside of the buttons), this make each `activity-row` a different width. Instead of that, I will choose to make each `activity-row` almost the width of the whole parent container by adding `width: 90%`. This allows for the `activity-row`s to not go all the way to the edges which would be ugly. (Seriously, try `100%` and see what I mean?)

Adding that alone already aligned our icons, stats, and buttons so first 3 tasks are done. Next, we want the icons, stats, and buttons to be vertically aligned within the row mostly so that `activity-stat` isn't stuck to the top of the `activity-row`. Since `activity-row` is already a `grid`, we can ask it to vertically center all elements with `align-items: center`. Easy peasy.

Hm, after reloading, it looks like that last line of code we added squished our button flat! By asking all items to be centered vertically in `activity-row`, we gave permission to `activity-row` to force its children elements down to their minimum height. This might not make sense and that is totally fine. We can override this by adding `height: 100%` to `activity-button` to bring it back to the height of its parent element.

Whew, last thing, the button. The text of the button is currently crammed into upper left corner of the button. We'll fix this by centering the things like we always do, asking the parent element to center its contents. The parent element to the text is `activity-button`. So we'll make `activity-button` a `grid` and ask it to `align-items` and `justify-items` to the `center`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      ...
      .interactive-area {
        background-color: #00BEBD;
        display: grid;
        align-items: center; /* This centers all elements inside of this element vertically */
        justify-items: center; /* This centers all elements inside of this element horizontally */
      }
      .activity-row {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr; /* This creates 3 columns of equal length */
        width: 90%; /* Makes this element almost as wide as the parent element */
        padding: 0 1rem;
        align-items: center;
      }
      .activity-icon {
        height: 40px;
        height: 40px;
      }
      .activity-button {
        background-color: #B27499;
        border-radius: 8px;
        box-shadow: 0 0 5px 0 grey;
        color: white;
        cursor: pointer;
        height: 100%;
        display: grid;
        justify-items: center;
        align-items: center;
      }
      ...
    </style>
  </head>
  ...
</html>
```

After all of these fixes, we get:

![]({{ site.baseurl }}/assets/img/module1/vp-interactive-5.png)

Wow! We did it! For a simple site, that sure did take a lot of tweaking to get things to look okay. Feel free to continue to make tweaks and improvements so that your site is something you like!

Here is the entirety of my code:

```
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        font-family: 'Courier New', Courier, monospace;
        font-weight: bold;
      }
      .header {
        padding: 32px;
      }
      .pet-name {
        font-size: 32px;
      }
      .main {
        display: grid; /* this tells `main` to be a grid*/
         /* the next line tells `main` that, since it is a grid now, to separate into 2 equal columns*/
        grid-template-columns: 1fr 1fr;
      }
      .image-area {
        background-color: #FFC292;
        display: grid;
        justify-items: center;
      }
      .pet-image {
        height: 500px;
        max-width: 100%;
        padding: 3rem;
      }
      .interactive-area {
        background-color: #00BEBD;
        display: grid;
        align-items: center; /* This centers all elements inside of this element vertically */
        justify-items: center; /* This centers all elements inside of this element horizontally */
      }
      .activity-row {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr; /* This creates 3 columns of equal length */
        width: 90%; /* Makes this element almost as wide as the parent element */
        padding: 0 1rem;
        align-items: center;
      }
      .activity-icon {
        height: 40px;
        height: 40px;
      }
      .activity-button {
        background-color: #B27499;
        border-radius: 8px;
        box-shadow: 0 0 5px 0 grey;
        color: white;
        cursor: pointer;
        height: 100%;
        display: grid;
        justify-items: center;
        align-items: center;
      }
    </style>
  </head>
  <body>
    <div class="header">
      <div class="pet-name">Big L</div>
      <div class="description">He is big and not good at things.</div>
    </div>
    <div class="main">
      <div class="image-area">
        <img class="pet-image" src="neutral.gif" />
      </div>
      <div class="interactive-area">

        <div class="activity-row">
          <img class="activity-icon" src="food.png" />
          <div class="activity-stat">100</div>
          <div class="activity-button">Eat fish</div>
        </div>
        <div class="activity-row">
          <img class="activity-icon" src="water.png" />
          <div class="activity-stat">50</div>
          <div class="activity-button">Drink water</div>
        </div>
        <div class="activity-row">
          <img class="activity-icon" src="exercise.png" />
          <div class="activity-stat">5</div>
          <div class="activity-button">Exercise</div>
        </div>

      </div>
    </div>
  </body>
</html>
```

## Conclusion

That was a lot of work just to get the site to a place where we like how it looks. However, it is exciting because now we have set ourselves up so that next time, we don't have to focus on the looks of things but instead just the functionality. How neat is that!?

![](https://media.tenor.com/images/2673ab05854a3825790732a4e7080cf1/tenor.gif)

