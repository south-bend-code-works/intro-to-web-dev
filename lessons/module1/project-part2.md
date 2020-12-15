---
layout: default
---

# Project Part 2: Virtual Pet

## Goal

At the end of this portion of the project, you will have completed the Virtual Pet project started in part 1. It will include 3 buttons that will increase (and decrease) your pet's stats. Your pet will "react" to it's state by changing it's image.
## Overview

Now that all of the "physical" components of your pet are in place, we now need to make the your page functional. As is, there are 3 buttons that do nothing, stats that don't change, and a static picture. We are going to use JavaScript to make this whole thing come to life. Prepare yourself. You're about to become the parent of a Virtual Pet.
## Steps

### Setup

Let's make sure we can see our project in the browser. Go to your desktop and find `virtual-pet`. Open that folder, right-click on `index.html`, and open in Chrome. If you see what we made in part 1, you're set.

Next, since we are going to add JavaScript to this page, we need a place to put it. The JS will go between `script` tags that will live just beneath your `body` tags.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
  <script>

  </script>
</html>
```

Once these are included, we are ready to start coding some JavaScript!

### Buttons

Last time, we made a button for each of the activities: eating, drinking, and exercising. Right now, if we click on any of the buttons, nothing happens. Let's change that.

