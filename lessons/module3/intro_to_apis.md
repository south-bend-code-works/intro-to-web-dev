---
layout: default
---

# Introduction to APIs

## What is an API

I'll be honest. When I think of APIs, I just think of those characters in video games that just stand around, waiting to be interacted with. You go up to them with a request or question and their sole purpose is to help you with a task or give you information.

However, that isn't a very technical answer to the question "What is an API?". I will let this excellent article bring you up to speed: [https://www.freecodecamp.org/news/what-is-an-api-in-english-please-b880a3214a82/](https://www.freecodecamp.org/news/what-is-an-api-in-english-please-b880a3214a82/)

## Using APIs

### Overview

Now that you have an overview of what APIs do in general, let's look at a few.

Copy and paste this code into an HTML file and then open it up on your browser:

```
<!DOCTYPE html>

<html>

  <body>
    <h1>Cat fact: <span id="cat-fact"></span></h1>
  </body>

  <script>

    var catFactEle = document.getElementById("cat-fact")

    var hitApi = (url) => {
      fetch(url)
        .then(res => res.json())
        .then(data => {
          catFactEle.innerHTML = data.text
        })
    }

    hitApi("https://cat-fact.herokuapp.com/facts/random?animal_type=cat")

  </script>

</html>
```

When you see the result of the code above, you should have many questions about what is happening.

Before taking an in depth look into the code, let's first talk about the API we are hitting in general.

In the code, you can see we have a function named `hitApi`. We call that function with the argument `"https://cat-fact.herokuapp.com/facts/random?animal_type=cat"`. If we copy and paste that url into our browser, we will get a result of something like this:

![ugly]({{ site.baseurl }}/assets/img/module3/api_ugly.png)

Not a very attractive website, is it? That's because that url didn't return an HTML file but instead it returned an **object**. We have seen and built **objects** in our code many times. **Objects** might not make good webpages but they are an excellent way to send data. If we look closely at what that url returned, we can see that most of the information isn't interesting to us. However, there is a **key/value** pair where the **key** is `text` and the **value** is string. That is the part that we are interested in for this API.

The API we are using above is from a site dedicated to random facts about animals, especially cats. Whoever created the site created an API that gives us random facts about cats. The way we access those facts is by using the url from above. That url is more than just a series of letters and symbols but it is actually a commmand which is *reach out to a certain server with certain instructions and bring back whatever it's response is*. Often, when we make requests to servers, they return HTML files but they don't have to. The url above returns instead an object. However, when we make these requests in JS, we don't have to display the raw **object**. Instead, we get the data that we want out of the object and use it however we want.

The object returned (written a little more legibly) is:

```
{
  "status":
    {
      "verified":true,
      "sentCount":1
    },
  "type":"cat",
  "deleted":false,
  "_id":"58e009420aac31001185ed11",
  "user":"58e007480aac31001185ecef",
  "text":"A cat's tongue has tiny barbs on it.",
  "__v":0,
  "source":"user",
  "updatedAt":"2020-09-03T20:20:01.808Z",
  "createdAt":"2018-03-13T20:20:02.622Z",
  "used":true
}
```

So, we can see that a lot of the information is useless to it but if we stored that object in a variable named `data`, we could access just the fact about cat with the code `data.text`. This is great because then we can use that `data.text` to display or whatever we want to do with it.

### The Code

Now that we understand these urls can return data **and** HTML files, we can now start looking at the code it takes to make use of these things.

In the code above, we have only a few things: a variable the references the `span` element with the id `cat-fact`, a function named `hitApi`, and a line that runs `hitApi`. Let's look into the function.

`hitApi` takes in a string as an argument. First in the function we see `fetch`. `fetch` is a function that is built into JS

## Conclusion