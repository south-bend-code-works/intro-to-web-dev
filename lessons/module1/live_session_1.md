---
layout: default
---

# Overview 

## Agenda
1. Review how the web works
    - Class Discussion
    - Show how chrome works
    - Backend / Front End (We are only on Front End for now)
2. HTML / CSS
    - What is HTML
    - Structure of an HTML Document
    - Friend-o-Gram
3. GIT / TERMINAL
4. Hosting your website on github
5. Review Final Project Part 1 (last 5 minutes)

## Zoom Links

### Section 1 (10am to 12pm)
<https://notredame.zoom.us/j/96545079849?pwd=K3psL1J4Q3FUNmxCbmpSa0pTbm9ndz09>

**Meeting ID: 965 4507 9849**

**Passcode: 835805**


### Section 2 (1pm to 3pm) 
<https://notredame.zoom.us/j/99670056329?pwd=OXRmSFNERU45Vi9ndkpJNUpGTFU1QT09>

**Meeting ID: 996 7005 6329**

**Passcode: 781595**

### Section 3 (4pm to 6pm) 
<https://notredame.zoom.us/j/92241686868?pwd=aHBiTmdOM25Eak52UEtOQU5XeDJvZz09>

**Meeting ID: 922 4168 6868**

**Passcode: 122449**

## Solution from Live Session

*Note: This was the solution we created to friend-o-gram in the live sessions for Sections 1 & 2.*

```
<!DOCTYPE html>

<html>

  <head>
    <style>
      .photo {
        height: 400px;
        background-size: cover;
      }

      .photo-holder {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
      }

      #photo-1 {
        background-image: url('photo-1.jpg')
      }

      #photo-2 {
        background-image: url('photo-2.jpg')
      }

      #photo-3 {
        background-image: url('photo-3.jpg');
        background-position: 50% 50%;
      }

      #photo-4 {
        background-image: url('photo-4.jpg')
      }

      #photo-5 {
        background-image: url('photo-5.jpg')
      }

      #photo-6 {
        background-image: url('photo-6.jpg')
      }
    </style>
  </head>

  <body>
    <h1>Friend-o-gram</h1>

    <div class="photo-holder">
      <div class="photo" id="photo-1"></div>
      <div class="photo" id="photo-2"></div>
      <div class="photo" id="photo-3"></div>
      <div class="photo" id="photo-4"></div>
      <div class="photo" id="photo-5"></div>
      <div class="photo" id="photo-6"></div>
    </div>

  </body>

</html>
```