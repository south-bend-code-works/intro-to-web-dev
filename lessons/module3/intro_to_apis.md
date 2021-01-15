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
        .then((res) => res.json())
        .then((data) => {
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

Not a very attractive website, is it? That's because that url didn't return an HTML file but instead it returned an **object**. We have seen and built **objects** in our code many times. **Objects** might not make good webpages but they are an excellent way to send data. If we look closely at what that url returned, we can see that most of the information isn't interesting to us. However, there is a **key/value** pair where the **key** is `text` and the **value** is a string. That string is the part that we are interested in for this API.

The API we are using above is from a site dedicated to random facts about animals, especially cats. Whoever created the site created an API that gives us random facts about cats. The way we access those facts is by using the url from above. That url is more than just a series of letters and symbols but it is actually a command which is *reach out to a certain server with certain instructions and bring back whatever it's response is*. Often, when we make requests to servers, they return HTML files but they don't have to. The url above returns instead an object. However, when we make these requests in JS, we don't have to display the raw **object**. Instead, we get the data that we want out of the object and use it however we want.

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

So, we can see that a lot of the information is useless to us but if we stored that object in a variable named `data`, we could access just the fact about cat with the code `data.text`. This is great because then we can use that `data.text` to display into our HTML or whatever we want to do with it.

### The Code

Now that we understand these urls can return data **and** HTML files, we can now start looking at the code it takes to make use of these things.

In the code above, we have only a few things: a variable that references the `span` element with the id `cat-fact`, a function named `hitApi`, and a line that runs `hitApi`. Let's look into that function.

`hitApi` takes in a string as an argument. First in the function body we see `fetch`. `fetch` is a function that is built into JS that allows us to make requests to other websites. 

Whenever you put a url in the search bar of your browser, you make a request to a server and then the results are displayed in your browser. Similarly, whenever you put a url into `fetch`, it makes a request to a server and then returns the data into a callback where we can use it in our JS.

So, we give `hitApi` a url, we use `fetch` and that url to make a request. That is what is happening in the line `fetch(url)`. Then, the first thing attached to that `fetch(url)` is `.then((res) => res.json())`. This line is a **callback** that says *whenever the data is returned from the server we just reached out to, please turn the data into a JavaScript object*. The reason we need to use this line is because the data that is initially returned from the server can be turned into other things that aren't **objects** but we will most often want the data to be turned into an **object** so we use `.then((res) => res.json())`.

Then, our last bit of code is the following:

```
.then((data) => {
  catFactEle.innerHTML = data.text
})
```

This is another callback that says *once the data is done being turned into a JS **object**, set the `innerHTML` of `catFactEle` to `data.text` (which is the value in the `data` that is our random fact about cats)*.

To recap, we first request data from a server by using `fetch` and a url. Then, we wait until the data is returned to use `.then((res) => res.json())` to turn that data into an **object**. Then, we wait until that is done to use that **object** to change our HTML to include the fact about a cat. 

The syntax and language around what we are doing may be confusing. Just remember the following: use `fetch` and a url to call an API, turn the data received into an object, do something with that object. The following can be used as a template for hitting APIs:

```
fetch("https://somewebsite.com/some_api_thing") // input actual url here
  .then((res) => res.json()) // turn data into an object here
  .then((dataObject) => {
    // do something with dataObject here
  })
```

### API Keys

Now that I have thrown an example at you, let's build one together.

First, we have to determine what we want to do. I think a website that would load a random picture of a cat would be really nice. So, I will first include an `img` element into my HTML that I have a place to place the image source we get from the API. I will give my `img` element the id `picture` so that I can reference it in my JS.


<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>

<html>

  <body>
    <img id="picture" />
  </body>

  ...

</html>
```

Now that I have a place to put an image, I can start focusing on my JavaScript.

Since I know that I will be changing the image source to my `#picture` element, I'm going to reference that element in my JS. I'm going to use the variable `pictureEle` to hold this reference at the top of my JS.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>

<html>

  ...

  <script>
    var pictureEle = document.getElementById("picture")
  </script>

</html>
```

So, I first have to find an API that returns cat pictures. After some research, it seems that [https://docs.thecatapi.com/](https://docs.thecatapi.com/) is a good choice. It has good documentation telling me how to use it and seems to be up to date.

A difference between this API and the cat-fact API is that this one requires an API key. In order to use this API, we have to include an API key whenever we use `fetch` and a url from this cat-image site. We get an API key by registering with the website. All I had to do was give the website my email and they sent me the API key to that email. 

Websites use API keys for a variety of reasons. Some APIs cost money to use them. By including an API key in the request to a website's server, that website can track how much I am using their API and charge me accordingly. However, the website we are going to use to get cat pictures doesn't charge money. The reason they want users to use an API key is so they can track how many users are using their API along with which of their users is using the API the most. If they didn't require an API key, anyone could their API. They wanted their site to be more secure and to track better stats so they require an API key.

Okay, so I got my API key in an email and it is `7f7e206f-5682-469d-9bf9-cd1e2ad1aa41`. You typically want to keep these API keys really safe but since we are only using a cat picture API, I feel okay showing you guys what an API key looks like. An API key is just a string made up of random numbers, letters, and symbols so that they are nearly impossible to guess.

Now that I have an API key, I am going to include my API key into my JS in a variable I will name `apiKey`.


<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>

<html>

  ...

  <script>
    var pictureEle = document.getElementById("picture")
    var apiKey = "7f7e206f-5682-469d-9bf9-cd1e2ad1aa41"
  </script>

</html>
```

Okay, so I have my API key stored in a variable in my JS. I now need to figure out which url will return random cat pictures. I visit the website and find [this page](https://docs.thecatapi.com/api-reference/images/images-search) which has great instructions for how to use this url to return random pictures of cats. It looks like I need to use the url `https://api.thecatapi.com/v1/images/search` and my API key. The site says the server will return an **array** with one **object** in it. This **object** will have a key named `url` which will have the image url we can use to put on our page. Sweet! Thanks good documentation for letting me know all of that!

Okay, now that I also have my url, I will create another variable named `url` that will hold the url I just talked about.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>

<html>

  ...

  <script>
    var pictureEle = document.getElementById("picture")
    var apiKey = "7f7e206f-5682-469d-9bf9-cd1e2ad1aa41"
    var url = "https://api.thecatapi.com/v1/images/search"
  </script>

</html>
```

Cool! I have my API key and my url. Now, I need to figure out how to include my API key into my call to the API. The documentation from the website says to include my API key as a **header** in my call. By including details in a **header** of a API call, we are able to securely send details like an API key or other credentials.

How do we include a **header** when using `fetch`. It turns out, `fetch` takes 2 arguments, a string (which is the url) and an **object** which includes **request options** which are basically instructions for how to make the API call.

In our request options, we can include a key **headers** which has the value of an **object**. In this object, we can include name and values of any **headers** we want to include. The website's documentation is telling me to include a header with the name `"x-api-key"` and the value of my API key. 

So, I am going to include a new variable in my JS called `requestOptions`, which is an **object**. `requestOptions` is going to be the second argument when I use `fetch`. Like I said before, a key we can include in `requestOptions` is `headers` whose value is another **object**. In this **object**, I will have `"x-api-key"` as my key and my API key as the value.

*Note: When using a key in an object that has dashes or spaces, the key must be a string.*

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>

<html>

  ...

  <script>
    var pictureEle = document.getElementById("picture")
    var apiKey = "7f7e206f-5682-469d-9bf9-cd1e2ad1aa41"
    var url = "https://api.thecatapi.com/v1/images/search"

    var requestOptions = {
      headers: {
        "x-api-key": apiKey,
      }
    }
  </script>

</html>
```

Sweet! I now have a `url` to use as my first argument for `fetch` and `requestOptions`, which includes my API key, as my second argument. Looks like I am ready to use `fetch`!

So, I will call `fetch` with `url` as the first argument and `requestOptions` as the second argument.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>

<html>

  ...

  <script>

    var pictureEle = document.getElementById("picture")
    var apiKey = "7f7e206f-5682-469d-9bf9-cd1e2ad1aa41"
    var url = "https://api.thecatapi.com/v1/images/search"

    var requestOptions = {
      headers: {
        "x-api-key": apiKey,
      }
    }

    fetch(url, requestOptions)

  </script>

</html>
```

If we refresh the page at this point, nothing seems to happen. That's because we made the call to the server but we need to include a **callback** to handle the data when it is returned. We do that by using the `.then` method and giving it a function.

Like we said before, the first **callback** we have to include when using `fetch` is `.then((res) => res.json())` which will turn the returned data into an **object** we can use. So, let's attach that line to the end of our `fetch` call.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>

<html>

  ...

  <script>

    var pictureEle = document.getElementById("picture")
    var apiKey = "7f7e206f-5682-469d-9bf9-cd1e2ad1aa41"
    var url = "https://api.thecatapi.com/v1/images/search"

    var requestOptions = {
      headers: {
        "x-api-key": apiKey,
      }
    }

    fetch(url, requestOptions)
      .then((res) => res.json())

  </script>

</html>
```

Now that we have one **callback** that turns the data into an **object**, we need to include yet another **callback** that has a function to use that **object** we just made. Again, we will attached the `.then` method to the end of this `fetch` call and give it a function that does something with the **object**. Let's first just use `console.log` to see what the data looks like.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>

<html>

  ...

  <script>

    var pictureEle = document.getElementById("picture")
    var apiKey = "7f7e206f-5682-469d-9bf9-cd1e2ad1aa41"
    var url = "https://api.thecatapi.com/v1/images/search"

    var requestOptions = {
      headers: {
        "x-api-key": apiKey,
      }
    }

    fetch(url, requestOptions)
      .then((res) => res.json())
      .then((data) => {
        console.log(JSON.stringify(data))
      })

  </script>

</html>
```

After printing that to my console, I see this:

```
[
  {
    "breeds":[],
    "id":"MTUxNTQwNQ",
    "url":"https://cdn2.thecatapi.com/images/MTUxNTQwNQ.jpg",
    "width":427,
    "height":640
  }
]
```

So, just like it said in the documentation, the API returned an **array** with one value in it which is an **object**. Inside that **object** is a key name `url` whose value is `"https://cdn2.thecatapi.com/images/MTUxNTQwNQ.jpg"` which is what we want to set the `.src` of our image to.

First, we need to get the **object** out of the **array**. I will create a new variable named `obj` and it's value will be the first value in the **array** `data`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>

<html>

  ...

  <script>

    var pictureEle = document.getElementById("picture")
    var apiKey = "7f7e206f-5682-469d-9bf9-cd1e2ad1aa41"
    var url = "https://api.thecatapi.com/v1/images/search"

    var requestOptions = {
      headers: {
        "x-api-key": apiKey,
      }
    }

    fetch(url, requestOptions)
      .then((res) => res.json())
      .then((data) => {
        
        var obj = data[0]
        
      })

  </script>

</html>
```

Next, I create another variable named `imageSrc` which will be set equal to the `url` of the `obj`.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>

<html>

  ...

  <script>

    var pictureEle = document.getElementById("picture")
    var apiKey = "7f7e206f-5682-469d-9bf9-cd1e2ad1aa41"
    var url = "https://api.thecatapi.com/v1/images/search"

    var requestOptions = {
      headers: {
        "x-api-key": apiKey,
      }
    }

    fetch(url, requestOptions)
      .then((res) => res.json())
      .then((data) => {

        var obj = data[0]
        var imageSrc = obj.url
        
      })

  </script>

</html>
```

Now that I have the url to the image of the cat in `imageSrc`, I will set that value equal to the `src` of our `img` element in our HTML.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<!DOCTYPE html>

<html>

  ...

  <script>

    var pictureEle = document.getElementById("picture")
    var apiKey = "7f7e206f-5682-469d-9bf9-cd1e2ad1aa41"
    var url = "https://api.thecatapi.com/v1/images/search"

    var requestOptions = {
      headers: {
        "x-api-key": apiKey,
      }
    }

    fetch(url, requestOptions)
      .then((res) => res.json())
      .then((data) => {

        var obj = data[0]
        var imageSrc = obj.url
        pictureEle.src = imageSrc
        
      })

  </script>

</html>
```

Wow! Now, everytime I refresh, I get a new picture of a cat on my screen. If that isn't happiness, I'm not sure what is.

## Conclusion

APIs are **not** an easy concept at all. Between API keys and callbacks, they can be downright frustrating even after being a developer for years! Please take time to slowly digest what is happening in the code above.

## Challenge

Truthfully, you will never feel like you know APIs until you use one on your own. Visit [this site](https://github.com/public-apis/public-apis) for a large list of free and open APIs. Choose one that seems interesting to you and create a small page to prove to yourself you can use these beautiful but difficult APIs.

