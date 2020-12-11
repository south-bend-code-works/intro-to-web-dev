---
layout: default
---

# Project Part 1: Virtual Pet

## Goal

The goal for this project is to begin building a Virtual Pet. At the end of both parts of this project, you will have a Virtual Pet that is needs food, water, and exercise and responds to how well balanced these needs are being handled. At the end, you will have built a webpage that looks something like this:

![](link-to-image.jpg)

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

