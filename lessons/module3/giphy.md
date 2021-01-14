---
layout: default
---


# Practice Problem: Giphy API

## Goal

The goal for this practice problem is to build a website that uses the [Giphy](https://giphy.com/) API to display a random gif for a topic.  

In addition, we will also show the JSON that the API returns on our website.

At the end of this activity, you will have developed something that looks like this:

![best example]({{ site.baseurl }}/assets/img/module3/giphy-api-example.gif)

## Overview

This activity will allow you to practice using APIs.  You will:
- Create a GIPHY Developer account and API Key
- Use the [GIPHY API Random Endpoint](https://developers.giphy.com/docs/api/endpoint#random) to return a random GIF for a topic
- Change the DOM on our website to show the GIF and the JSON the API returned.

## Instructions
### About the Giphy API


### Create your GIPHY Developer Account and API Key
Follow these steps to get your API Key.

1. Go to https://developers.giphy.com/
2. Create an account and login.
3. Press "GET STARTED" and then "CREATE AN APP"
4. Click the "Create App" button to get assigned an API Key.  
    1. Select the "API"
    2. Give your App a name & description
5. Copy your API key into your clipboard.

If you want to learn more, you should also check out this [giphy quickstart guide](https://developers.giphy.com/docs/api#quick-start-guide).

### Starter Code
First things first, you need to create a new folder called 'giphy' and place an index.html file into it.  Use the starter HTML code provided below to jump start you.

{: .hint-content}

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
            const submitButton = document.getElementById("submit")
            const image = document.getElementById("gif")
            const topicTextField = document.getElementById("topic")
            const pre = document.getElementById("responseJson")
        </script>
    </body>
</html>
```

### About the GIPHY APIs

https://developers.giphy.com/docs/api/schema#gif-object
https://developers.giphy.com/docs/api#response-codes
https://developers.giphy.com/explorer

#### The Giphy random API
GIPHY random gives you instant access a single random gif that matches the tag you provided.  By entering a word or phrase you'll get a gif matches.

### Calling the GIPHY API from JavaScript

```
const apiKey = 'HXKNHt1i1gYbHKVb3bJfeYVBVLRlSqhI'
            var base_url = 'https://api.giphy.com/v1/gifs/random?api_key=HXKNHt1i1gYbHKVb3bJfeYVBVLRlSqhI&rating=g&lang=en&tag=' + topicTextField
            
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
```

### Conclusion


<div class="hint">Hover for Completed Solution</div>

{: .hint-content}

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
            const submitButton = document.getElementById("submit")
            const image = document.getElementById("gif")
            const topicTextField = document.getElementById("topic")
            const pre = document.getElementById("responseJson")

            const apiKey = 'HXKNHt1i1gYbHKVb3bJfeYVBVLRlSqhI'
            var base_url = 'https://api.giphy.com/v1/gifs/random?api_key=HXKNHt1i1gYbHKVb3bJfeYVBVLRlSqhI&rating=g&lang=en&tag=' + topicTextField
            
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