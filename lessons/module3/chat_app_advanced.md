---
layout: default
---

# Project Part 1: Advanced Chat App


## Goal

There are two goals for this phase of our chat app project:

1. Allow users to send a gif using the giphy API.
2.  Style your chat application

# Part 1: Add support for gifs

A picture is worth a thousand words, so let's update our chat application so that you can send an appropriate gif instead of a text message.

To do this we will use the /giphy API
If the user types "/giphy cats" in the chat, then the chat app will select a random cat gif and send it in the chat.

### GIPHY API

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