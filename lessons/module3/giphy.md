---
layout: default
---

# Practice Problem: Giphy API

## Goal

The goal for this practice problem is to build a website that uses the [Giphy](https://giphy.com/) API to display a random gif for a topic.  

In addition, we will also print the JSON that the API returns on our website.

At the end of this activity, you will have developed something that looks like this:

![best example]({{ site.baseurl }}/assets/img/module3/giphy-api-example.gif)

You will:
- Create a GIPHY Developer account and API Key
- Use the [GIPHY API Random Endpoint](https://developers.giphy.com/docs/api/endpoint#random) to return a random GIF for a topic
- Change the DOM on our website to show the GIF and the resulting JSON the API returned.

## Instructions

### Create your GIPHY Developer Account and API Key
Follow these steps to get your API Key.

1. Go to [https://developers.giphy.com/](https://developers.giphy.com/)
2. Create an account and login.
3. Press "GET STARTED" and then "CREATE AN APP"
4. Click the "Create App" button to get assigned an API Key.  
    1. Select the "API"
    2. Give your App a name & description
5. Copy your API key into your clipboard.

If you want to learn more, you should also check out this [giphy quickstart guide](https://developers.giphy.com/docs/api#quick-start-guide).

### Starter Code
Create a new folder called 'giphy' and place an index.html file into it.  Use the starter HTML code provided below.

Note: Their is a `<pre>` html element in the starter code.  It's like a `<div>` except that it preserves all formatting such as spaces and tabs.  We will use this to print our pretty print JSON object so it's easy to read. 

```
<!DOCTYPE html>
<html>
    <head>
        <title>Giphy API</title>
        <meta charset="utf-8"/>
        <style>
            img {display:block;
                margin:15px}
            pre { font-family: monospace; 
                background-color: black;
                color: whitesmoke;
                padding: 10px;
                margin: 10px;
            }
        </style>
    </head>
    <body>
        <h1>Find a random gif for this topic</h1>
        <label>Topic</label>
        <input id="topic"/>
        <button id="submit">Submit</button>
        <img id="gif" src="https://media.giphy.com/media/nJ6yoH4nBNCBa/giphy.gif"/>
        <div>"Powered By GIPHY"</div>

        <H2>API Result</H2>

        <!---The pre tag preserves all formatting such as spaces and tabs-->
        <pre id="responseJson">The data the API returns will display here</pre>

        <script>
            var submitButton = document.getElementById("submit")
            var image = document.getElementById("gif")
            var topicTextField = document.getElementById("topic")
            var pre = document.getElementById("responseJson")
        </script>
    </body>
</html>
```

### About the GIPHY APIs

Before we start writing our JavaScript, take a moment to read the documentation about the GIPHY API.

Specifically, we will be using the [Random API Endpoint](https://developers.giphy.com/docs/api/endpoint#random).

This API will return a gif-object, which is a JSON document.  The fields in that JSON document are described [here](https://developers.giphy.com/docs/api/schema#gif-object).

Furthermore, we are using a non-production API key which is rate limited.  This means that if we overuse the API or use it too quickly, it might temporarily deny our requests so we don't overwhelm Giphy's servers.  This can cause the API to send back a failed [response code](https://developers.giphy.com/docs/api#response-codes).

Finally, take a second to try out the API directly in the browser.  Pay special attention to how the URL is formed.  We will be programmatically creating our own url, so it's helpful to see what it should look like.  Use the [API explorer](https://developers.giphy.com/explorer) to test out the API.

### Calling the GIPHY API from JavaScript

Now we are ready to call the Random GIF API endpoint from our program.  The first thing we need to do is wire up our submitButton using addEventListner().  We've done this before, but if you can't remember feel free to check out the solution.

Once we have added our EventListener we need to build our URL to call the API.  Because most of the URL is constant, we can put that in a base URL.  Then, anytime we want to search for a new tag we just need to append that text.  Notice that each argument in our API is separated by a `&`.

```
var base_url = 'https://api.giphy.com/v1/gifs/random?api_key=YOUR-API-KEY-HERE&rating=g&lang=en&tag='
var search_tag = 'cat'
```

There is one big gotcha when building URLs; URLS cannot contain spaces and other special characters.  To get around this, we do something called URI encoding.

```
var invalid_search_tag = 'cat lover' // This would create an invalid URL because of the space.
var valid_search_tag = encodeURI('cat lover) // This would create the valid URIencoded string: "cat%20lover"
```

Once we have the URL for our API, we simply need to make an HTTP request and the API will return some data as JSON for us to process.

To make an API request in JavaScript we will use the fetch() function. Recall that fetch() returns a promise that returns a promise, so you have this slightly awkward double .then() pattern.  The code we need is below.  Add it to the function that runs when our button is clicked.

```
// Use the JavaScript fetch API
fetch(url)
.then(response => response.json())
.then(myJson => {
    console.log(myJson)
})
```

Take a moment to look at the console logging for the object returned.

Amazing!  Now that we have a result from our API, we simply need to set the `src` attribute of our `<img>` to the url for the image.  If you look at the schema for the json returned, you will see that the field we want is called `image_url`.  

```
image.src = myJson.data.image_url
```

Last but not least, let's also print the entire JSON object that the API returned on our webpage to make it crystal clear what data the API returned.  We'll need to use a special function to turn our JavaScript object into a formatted string.

```
pre.innerHTML = JSON.stringify(myJson, null, 2); // Pretty Print the 
```

And that is about it!  


### Conclusion
At this point you should have a program that finds a random gif!  Super neat.

<div class="hint">Hover for Completed Solution</div>

{: .hint-content}

```
<!DOCTYPE html>
<html>
    <head>
        <title>Giphy API</title>
        <meta charset="utf-8"/>
        <style>
            img {
              display:block;
              margin:15px
            }
            pre {
              font-family: monospace; 
              background-color: black;
              color: whitesmoke;
              padding: 10px;
              margin: 10px;
            }
        </style>
    </head>
    <body>
        <h1>Find a random gif for this topic</h1>
        <label>Topic</label>
        <input id="topic"/>
        <button id="submit">Submit</button>
        <img id="gif" src="https://media.giphy.com/media/nJ6yoH4nBNCBa/giphy.gif"/>
        <div>"Powered By GIPHY"</div>

        <H2>API Result</H2>

        <!---The pre tag preserves all formatting such as spaces and tabs-->
        <pre id="responseJson">The data the API returns will display here</pre>

        <script>
            var submitButton = document.getElementById("submit")
            var image = document.getElementById("gif")
            var topicTextField = document.getElementById("topic")
            var pre = document.getElementById("responseJson")

            var apiKey = 'YOUR-API-KEY-HERE'
            var base_url = 'https://api.giphy.com/v1/gifs/random?api_key=' + apiKey + '&rating=g&lang=en&tag='
            
            submitButton.addEventListener("click", function() {
                url = base_url + encodeURI(topicTextField.value)
                
                // User the JavaScript fetch API
                fetch(url)
                .then(response => response.json())
                .then(myJson => {
                  image.src = myJson.data.image_url
                  pre.innerHTML = JSON.stringify(myJson, null, 2); // Pretty Print the 
                })
            })
        </script>
    </body>
</html>
```