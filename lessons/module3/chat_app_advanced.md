---
layout: default
---

# Project Part 1: Advanced Chat App


## Goal

A picture is worth a thousand words, so let's update our chat application so that you can send an appropriate gif instead of a text message.

Goals:
1. Allow users to send a gif using the giphy API.
2. Style your chat application

## Getting Started

### Create your Advanced Chat Project Folder
First, duplicate your project folder for simple chat and name it advanced chat.  It's a good idea to make a copy.

### 
To do this we will use the Random GIF API endpoint from our practice problem.  The code to call that API was:

```
const apiKey = 'YOUR-API-KEY-HERE'
var base_url = 'https://api.giphy.com/v1/gifs/random?api_key=' + apiKey + '&rating=g&lang=en&tag='
url = base_url + 'INSERT TAG KEYWORD'

// User the JavaScript fetch API
fetch(url)
.then(response => response.json())
.then(myJson => {
  console.log(myJson)
})       
```


## GIPHY API

1. Go to https://developers.giphy.com/
2. Create an account and login.
3. Press "GET STARTED" and then "CREATE AN APP"
4. Click the "Create App" button to get assigned an API Key.  
    1. Select the "API"
    2. Give your App a name & description
5. Copy your API key into your clipboard.

var hitApi = (url) => {
              fetch(url)
                .then(res => res.json())
                .then(data => {
                  catFactEle.innerHTML = data.text
                })
            }

hitApi("https://cat-fact.herokuapp.com/facts/random?animal_type=cat")

## Part 2: Style your application
Use your creativity to ...

# Conclusion
asef