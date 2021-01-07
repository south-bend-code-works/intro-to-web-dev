---
layout: default
---

# Intro to Databases

## Goal
By the end of this lesson, you will have:

1. An understanding of why databases are important.
2. The fundamental concepts behind Google's Firestore database.

## Why are Databases Important?

Previously, all of the content we displayed in our webpages was *hard-coded* into our HTML document.  While this may work for static websites, it won't work for more sophisticated applications, such as online stores.

The web uses HTTP, which is a "stateless protocol".  This is fancy speak for "If you refresh your web-browser any changes you made will be lost".  In the early days of the web, this was not too bad as we were mostly using the web to share research papers and pictures of our cats.  As time passed, the complexity of our web applications increased and we began to need to save the "state" of the site so we could recall it again later; this doesn't play nice with a stateless http protocol.  For example, an online store needs to save the items we've added to our cart so we can purchase them later.

To do save the "state", developers came up with a number of different ways to store data.  For example, you may have heard of __cookies__, which are saved in your web browser; these cookies are basically tiny text files that developers use to store the "state of things" for later.  When a website loads, we can check if a cookie exists, and if so, use any data that was stored in it.  For example, we could save a list of all the items in our shopping cart into a cookie.  Unfortunately, cookies have a __major__ drawback in that they are not very useful if you are using more than one device or browser.

We use __databases__ to persist data across multiple devices.  By storing our data, like the items in our shopping cart, in a centralized database we solve the problem that we ran into with cookies.  With a database, no mater which device or browser we use, we can load all of the items in our cart so the user can pick right back up where we left off.

This diagram below illustrates how a database can be used to power an online store.  Notice the database is shared between multiple devices!

![shopping cart database]({{ site.baseurl }}/assets/img/module2/database-example.png)

## About Google Firestore

At this point you might be thinking, wow, it would be great if I had a database!  You are right, having a database does make you cool.  Lucky for us, Google has built `Firestore`; a super cool, scaleable, cloud based database that we can get started with for free.

### Introducing Google Firestore
<iframe width="560" height="315" src="https://www.youtube.com/embed/QcsAb2RR52c" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### What is a document store database?
This video explains how firebase stores your data.  The biggest concept you need to understand is that Firebase

### Conclusion

You've now got the basics of why we need a database and you've been introduced Firestore.  Congrats!

<iframe src="https://giphy.com/embed/OcZp0maz6ALok" width="480" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/30-rock-liz-lemon-i-love-this-show-OcZp0maz6ALok">via GIPHY</a></p>