---
layout: default
---

# Project Part 2: Advanced Chat App


## Goal

A picture is worth a thousand words.  The goal for this project is to add the ability to send an animated gif within our chat application.  We'll base this project on our existing simple chat project and use the GIPHY api.  Durning this project you will:

1. Allow users to send a gif using the giphy API by typing `/giphy topic`
2. Style your chat application

Here is what sending a gif will look like:

![chat example]({{ site.baseurl }}/assets/img/module3/advanced_chat_example.gif)

## Getting Started

### Create your Advanced Chat Project Folder
* Create a new folder called "Advanced Chat"
* Create a blank index.html file.
* Copy and paste the following starter code into your index.html file.  
  * This was based on our previous simple chat project.
  * Update the API Keys with your projects Keys.
  * <b>No messages will be sent/received yet, we will be recoding this bit</b>

<div class="hint">Hover for Starter Code</div>

{: .hint-content}
```
<!DOCTYPE html>
<html>

<head>
	<title>Advanced Chat</title>
	<meta charset="utf-8"  />
</head>

<body>
    <!-- The core Firebase JS SDK is always required and must be listed first -->
    <script src="https://www.gstatic.com/firebasejs/8.2.1/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/8.2.1/firebase-firestore.js"></script>

    <h1>Advanced Chat</h1>
    <ul>
        <li>Type any text to send a message, or</li>
        <li>Type /giphy into the message box to send a random gif (e.g. /giphy cat)</li>
    </ul>
    <label>Username:</label>
    <input type="text" id="username" placeholder="Rick">
    
    <label>Message:</label>
    <input type="text" id="message" placeholder="Hi Morty">
    
    <button id="send">Send</button>
    
    <h3>Chat Messages:</h3>

    <div id="messagesContainer">
        <!-- We will display any messages here that we send/retrieve from Firestore -->
    </div>

     <script>

        // ---------------------------------------
        // Initialize Firebase and Firestore
        // ---------------------------------------

        // Replace with your web app's Firebase configuration
        var firebaseConfig = {
            apiKey: "AIzaSyCzd22PWoCipek5E-7qDx-WfFmBO0hjb6g",
            authDomain: "intro-to-webdev-chat-app.firebaseapp.com",
            projectId: "intro-to-webdev-chat-app",
            storageBucket: "intro-to-webdev-chat-app.appspot.com",
            messagingSenderId: "556658533694",
            appId: "1:556658533694:web:d26d93919b6280d7efb86f"
        };

        // Initialize our application
        firebase.initializeApp(firebaseConfig);
        var firestore = firebase.firestore();

        var collectionRef = firestore.collection('messages')

        // Inputs
        var inputUsername = document.getElementById("username")
        var inputMessage = document.getElementById("message")
        var sendButton = document.getElementById("send")

        // Output DIV
        var messagesContainer = document.getElementById("messagesContainer")

        // Giphy API
        var apiKey = 'HXKNHt1i1gYbHKVb3bJfeYVBVLRlSqhI'
        var base_url = 'https://api.giphy.com/v1/gifs/random?api_key=' + apiKey + '&rating=g&lang=en&tag='

        // TODO: Define a helper function to save our message to FireStore
        var saveMessageToFirestore = (username, textToSave, bGiphyURL) => {
          //TO DO: add the code to add the document to our collection using collectionRef.add()
        }

        // Add an event listener to our button that adds a new message to our firestore collection
        sendButton.addEventListener("click", () => {                
            // TODO: Respond to the send button being pressed
        })

        // Define a function to listen for real-time updates
        var getRealTimeUpdates = () => {
            
            // All documents in our collection, messages, ordered from oldest to newest
            var collectionQuery = firestore.collection('messages').orderBy('timestamp', 'asc')

            collectionQuery.onSnapshot((snapshot) => {                
                // Each snapshot contains one or more DocumentChange objects
                // Loop through each document change
                snapshot.docChanges().forEach((docChange) => {

                    // Log the document change we detected
                    console.log(docChange)

                    // get the data for this document
                    var data = docChange.doc.data()
       
                    // Create a new div with this username and message as the content.
                    var div = document.createElement("DIV");   // Create a new <div> element
                    div.innerHTML = data.username + ": " + data.txt; // Insert text for our username and message
                    messagesContainer.appendChild(div); 
                });
            });
        }

        // Call our function to start listening for real-time updates
        getRealTimeUpdates();

      </script>
</body>
</html>
```

### Add Support for the giphy command.
Previously, we would simply save the text that the user typed to Firestore.  However, the `/giphy` feature makes things a tad more complicated.

Let's think about how the application needs to work:

* When we have a `standard message` we can simply it save to Firestore
* When we have the `/giphy` command we need to find an appropriate GIF and save it's URL to Firestore

In order to determine if we have a `/giphy` command we need to check if our `inputMessage` starts with `/giphy`.

In Javascript, there are a number of ways to detect if a string starts with another string.  In this case, we will use the .indexOf("somestring") function which returns the index position in the string where the substring was found.

For example, `"A big cat".indexOf("big")` would return an index of 2.  Because indexes start with zero, we can see that the string "big" was found at the 3rd position in our string `"A big cat".

Based on this, we know a string starts with `/giphy` when `indexOf("/giphy")` returns 0.

#### Code it
Update our sendButton.addEventListener() function to log to the console if the message starts with `/giphy`.

<div class="hint">Hover for hint</div>

{: .hint-content}

```
sendButton.addEventListener("click", () => {     
  
  txt = inputMessage.value

  if(txt.indexOf('/giphy') == 0) {
    console.log("Found Giphy Command at the start of the txt string")
  } else {
    console.log("Didn't find Giphy Command at the start of the txt string")
  }
})
```

#### Plan it
Let's pause for a minute to think about what happens next. 

* When we have a `\giphy` command:
  * We need to parse out the topic, so for `\giphy cat` we need to get the string `cat`
  * We need to call the giphy API to find a random gif of a cat
  * We need to save the URL for that gif into our Firestore database as the message text
  * We need to set some type of flag in Firestore to indicate that this message is a URL for an image.
* When we have standard txt message
  * We want to save the txt message to firebase

In either case, we are saving a message to firebase.  We don't want to repeat this "saving" code, so let's write a helper function to save data to Firestore that we can easily call over and over.

This code is provided for you.  Add it towards the top of your script, just before your call to addListener()

```
var saveMessageToFirestore = (username, textToSave, bGiphyURL) => {
  collectionRef.add({
      username: username,
      txt: textToSave,
      timestamp: Date.now(),
      bGiphyURL: bGiphyURL //THIS NEW FIELD TELLS US IF WE ARE SAVING A URL OR A TXT MESSAGE
  }).then(() => {
      console.log("Message Saved!");
  }).catch((error) => {
      console.log("Got and error:", error);
  });
}
```

Notice that this code is pretty much the same as before in simple chat, except for the new field called bGiphyURL.  This field is called a "flag" and it's used to indicate if this document is a standard message or a URL for a GIF.  It's a boolean variable (e.g. true or false).

#### Code it: Update AddEventListener() to use our helper function
Great, now that we have defined our helper function let's use it!

1. In our addEventListener(), if we have a GIPHY command
  * Extract the topic using substring()  For example: `"\giphy cat".substring(7)` will return `"cat"`
  * Call our GIPHY API to get a Random GIF URL.  Use fetch() and feel free to reference your previous code from our GHIPY API practice problem.
  * Save the GIF URL as the txt message using saveMessageToFirestore()
2. We have a standard message
  * Simply call saveMessageToFirestore() with the message text.

<div class="hint">Hover for Hint</div>

{: .hint-content}

```
sendButton.addEventListener("click", () => {                            
    txt = inputMessage.value
    // If the messages contains the '/giphy' only send the URL to the gif!
    if(txt.indexOf('/giphy') == 0) {
        console.log("String starts with the giphy command" + txt.indexOf('/giphy'))
        
        txt = txt.substring(7); // '/giphy ' is 7 characters long

        url = base_url + encodeURI(txt)
    
        // User the JavaScript fetch API
        fetch(url)
        .then(response => response.json())
        .then(myJson => {
            saveMessageToFirestore(inputUsername.value, myJson.data.image_url, true)
        })
        
    } else {
        saveMessageToFirestore(inputUsername.value, inputMessage.value, false)
    }
})
```

### Try it
Sadly, our application is still only printing the URLS to the screen:

![chat so far]({{ site.baseurl }}/assets/img/module3/advanced_chat_progress.png)

In order to get these to display as images, we need to add a `<img>` tag when we have a GIPHY URL (use the bGiphyURL field in firestore)

### Code it: Add `<img>` tags to the DOM for giphy gifs.
Modify your getRealTimeUpdates() function to add an `<img>` div with the `src` set to the URL for GIPHY gifs.  This `<img>` div should be a child element of our new `<div>` that contains the username.

<div class="hint">Hover for Hint</div>

{: .hint-content}

```
// Define a function to listen for real-time updates
var getRealTimeUpdates = () => {
    
    // All documents in our collection, messages, ordered from oldest to newest
    var collectionQuery = firestore.collection('messages').orderBy('timestamp', 'asc')

    collectionQuery.onSnapshot((snapshot) => {                
        // Each snapshot contains one or more DocumentChange objects
        // Loop through each document change
        snapshot.docChanges().forEach((docChange) => {

            // Log the document change we detected
            console.log(docChange)

            // get the data for this document
            var data = docChange.doc.data()

            if(data.bGiphyURL) {
                // Create a div with this username and message IMAGE the content.
                
                var div = document.createElement("DIV");   // Create a new <div> element
                div.innerHTML = data.username + ": "; // Insert text for our username and message

                var img = document.createElement("IMG");
                img.src = data.txt
                div.appendChild(img)
                messagesContainer.appendChild(div); 
            } else {
                // Create a div with this username and message TEXT the content.
                var div = document.createElement("DIV");   // Create a new <div> element
                div.innerHTML = data.username + ": " + data.txt; // Insert text for our username and message
                messagesContainer.appendChild(div); 
            }                    
        });
    });
}
```

### Complete Solution for giphy support

Awesome, at this point you should have an application that can send either images or text! Pretty amazing.

Below is the complete solution to the `/giphy` functionality challenge.

<div class="hint">Hover for Solution</div>

{: .hint-content}

```
<!DOCTYPE html>
<html>

<head>
	<title>Advanced Chat</title>
	<meta charset="utf-8"  />
</head>

<body>
    <!-- The core Firebase JS SDK is always required and must be listed first -->
    <script src="https://www.gstatic.com/firebasejs/8.2.1/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/8.2.1/firebase-firestore.js"></script>

    <h1>Advanced Chat</h1>
    <ul>
        <li>Type any text to send a message, or</li>
        <li>Type /giphy into the message box to send a random gif (e.g. /giphy cat)</li>
    </ul>
    <label>Username:</label>
    <input type="text" id="username" placeholder="Rick">
    
    <label>Message:</label>
    <input type="text" id="message" placeholder="Hi Morty">
    
    <button id="send">Send</button>
    
    <h3>Chat Messages:</h3>

    <div id="messagesContainer">
        <!-- We will display any messages here that we send/retrieve from Firestore -->
    </div>

     <script>

        // ---------------------------------------
        // Initialize Firebase and Firestore
        // ---------------------------------------

        // Replace with your web app's Firebase configuration
        var firebaseConfig = {
            apiKey: "AIzaSyCzd22PWoCipek5E-7qDx-WfFmBO0hjb6g",
            authDomain: "intro-to-webdev-chat-app.firebaseapp.com",
            projectId: "intro-to-webdev-chat-app",
            storageBucket: "intro-to-webdev-chat-app.appspot.com",
            messagingSenderId: "556658533694",
            appId: "1:556658533694:web:d26d93919b6280d7efb86f"
        };

        // Initialize our application
        firebase.initializeApp(firebaseConfig);
        var firestore = firebase.firestore();

        var collectionRef = firestore.collection('messages')

        // Inputs
        var inputUsername = document.getElementById("username")
        var inputMessage = document.getElementById("message")
        var sendButton = document.getElementById("send")

        // Output DIV
        var messagesContainer = document.getElementById("messagesContainer")

        // Giphy API
        var apiKey = 'HXKNHt1i1gYbHKVb3bJfeYVBVLRlSqhI'
        var base_url = 'https://api.giphy.com/v1/gifs/random?api_key=' + apiKey + '&rating=g&lang=en&tag='

        // Helper function to save our message to FireStore
        var saveMessageToFirestore = (username, textToSave, bGiphyURL) => {
            collectionRef.add({
                    username: username,
                    txt: textToSave,
                    timestamp: Date.now(),
                    bGiphyURL: bGiphyURL
                }).then(() => {
                    console.log("Message Saved!");
                }).catch((error) => {
                    console.log("Got and error:", error);
                });
        }

        // Add an event listener to our button that adds a new message to our firestore collection
        sendButton.addEventListener("click", () => {                
            
            txt = inputMessage.value
            // If the messages contains the '/giphy' only send the URL to the gif!
            if(txt.indexOf('/giphy') == 0) {
                console.log("String starts with the giphy command" + txt.indexOf('/giphy'))
                
                txt = txt.substring(7); // '/giphy ' is 7 characters long

                url = base_url + encodeURI(txt)
            
                // User the JavaScript fetch API
                fetch(url)
                .then(response => response.json())
                .then(myJson => {
                    saveMessageToFirestore(inputUsername.value, myJson.data.image_url, true)
                })
                
            } else {
                saveMessageToFirestore(inputUsername.value, inputMessage.value, false)
            }
        })

        // Define a function to listen for real-time updates
        var getRealTimeUpdates = () => {
            
            // All documents in our collection, messages, ordered from oldest to newest
            var collectionQuery = firestore.collection('messages').orderBy('timestamp', 'asc')

            collectionQuery.onSnapshot((snapshot) => {                
                // Each snapshot contains one or more DocumentChange objects
                // Loop through each document change
                snapshot.docChanges().forEach((docChange) => {

                    // Log the document change we detected
                    console.log(docChange)

                    // get the data for this document
                    var data = docChange.doc.data()
        
                    if(data.bGiphyURL) {
                        // Create a div with this username and message IMAGE the content.
                        
                        var div = document.createElement("DIV");   // Create a new <div> element
                        div.innerHTML = data.username + ": "; // Insert text for our username and message

                        var img = document.createElement("IMG");
                        img.src = data.txt
                        div.appendChild(img)
                        messagesContainer.appendChild(div); 
                    } else {
                        // Create a div with this username and message TEXT the content.
                        var div = document.createElement("DIV");   // Create a new <div> element
                        div.innerHTML = data.username + ": " + data.txt; // Insert text for our username and message
                        messagesContainer.appendChild(div); 
                    }                    
                });
            });
        }

        // Call our function to start listening for real-time updates
        getRealTimeUpdates();

      </script>
</body>
</html>
```

## Part 2: Style your application
At this point your application's core functionality should be done.  Use CSS to add your own style to your chat application.  There are not instructions for this part of the assignment.  Use your own creativity to style the chat anyway you would like!

## Conclusion

Congratulations!  You have developed a fairly sophisticated and gorgeous chat application, great work!

