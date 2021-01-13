---
layout: default
---

# Project Part 1: Simple Chat App

## Goal

Our goal for this project is to build a simple, web-based chat app.  Our Chat app will:
- Allow anyone on our website to post a new message.
- Listen for messages posted by others and display them on them on our screen.

At the end of this activity, we will have built something similar to this example of Rick chatting with Morty.

![chat example]({{ site.baseurl }}/assets/img/module2/simple-chat-1.0-animated.gif)


### Starter Code

1. Create a a folder called chat-app and save the following code in your index.html file.
2. Paste your projects `firebaseConfig` values into the starter script to replace the `...`.  
     - Note: You'll also need to make sure that the version numbers (e.g. 8.2.1) for your Firebase JS SDK match what you see in your project settings.
 
```
<!DOCTYPE html>
<html>

<head>
    <title>Simple Chat App</title>
    <meta charset="utf-8"  />
</head>

<body>
    <!-- The core Firebase JS SDK is always required and must be listed first -->
    <script src="https://www.gstatic.com/firebasejs/8.2.1/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/8.2.1/firebase-firestore.js"></script>


     <p>… Your HTML content here …</p>

     <script>
        // Your web app's Firebase configuration
        var firebaseConfig = {
          apiKey: ...,
          authDomain: ...,
          projectId: ...,
          storageBucket: ...,
          messagingSenderId: ...,
          appId: ...
        };

        // Initialize Firebase
        firebase.initializeApp(firebaseConfig);

        // Store a reference to firestore as db (for convienence)
        var db = firebase.firestore();

        //--------------
        // saveMessage
        //--------------
        function saveMessage(messageText) {
            // TODO: get the username & message from the DOM
              
            // TODO: save our message to firebse
            
        }

        //--------------
        // getRealtimeUpdates
        //--------------
        getRealtimeUpdates = function() {
          
        }

      </script>
</body>
</html>
```

#### Try it out
* Open your page in Chrome.
* You'll see the text input boxes and the button for our app, but nothing will work yet!

### Send a message

<p>Let's pause here and think about what needs to happen.  How will we get messages from one computer to another? If you said, let's use the Database, then you are correct!</p>

Often, it helps to write out each step we need to take.
1. The user will type in the username and message
2. Capture the username and message from the DOM using JavaScript
3. Save the username and message as a new document in a collection.  Let's call the collection 'messages'
4. 
<p>First, one of the users needs to send a message to the database.    The message needs the following information:

```
{
         "username":"chris"
         "msg":42,
         "timestamp":"M",
         "books":[
            "Game of Thrones",
            "Ready Player One"
         ]
      },
```


To store the chat messages that are written by users, we'll use our Firestore Database.

To add the functionality for users to write messages to our database, we will create a new function called `saveMessage()`

Because we have already initialized firebase using our web app's credentials, we can easily reference to our database as: `firebase.firestore`.  To make our code easier to read, we will create a new connivence variable called `db` that we set equal to `firebase.firestore`

Recall that in Firestore, our database is simply a collection of documents.  W

For our chat application, we only need one collection, let's call it `messages`.

```db.collection('messages')```

Once we have our collection, we want to add a document to that.  There are several ways to create a new document inside of a collection, which is documented here: https://firebase.google.com/docs/firestore/manage-data/add-data.

Every document in our collection has to have a meaningful ID that identifies it, and in the case of our chat application it's more convenient to let Cloud Firestore auto-generate that ID for us. As the documentation points out, this can done for us by calling add().  add() takes one argument, which is a dictionary of keys and values. 

```
// A dictionary with key:value pairs.  The key is the field name in our document and the value is what it's set to.
new_message = {
    username: "Rick",
    text: "You realize that nighttime makes up half of all time?"
}

db.collection('messages').add(new_message)
```

#### Try it out
* Reload your updated `chat-app.html` in your browser.
* Type in a user name and a message and click "send".
* In another tab, open your firebase console and click on Firestore.
* You should see a new collection, called 'messages', with one or more documents that reflect your messages!

Sadly, no messages show up yet in our webpage.  That is because we have to tell our client-side code to listen for new messages from the database.  Let's do that next.

### 5. Synchronize messages
While we have 
To read messages in the app, we'll need to add listeners that trigger when data changes and then create a UI element that shows new messages.

We'll add code that listens for newly added messages from the app. In this code, we'll register the listener that listens for changes made to the data. We'll only display the last 12 messages of the chat to avoid displaying a very long history upon loading.

Go back to the file public/scripts/main.js.
Find the function loadMessages.
Replace the entire function with the following code.
* Right-Click and download the following images 
* Save them in a new sub-folder, `imgs`, in your `quidditch-cup` project directory.

Quaffle            |  Golden Snitch
:-------------------------:|:-------------------------:
![]({{ site.baseurl }}/assets/img/module1/quidditch-assets/quaffle64x64.png)  |  ![]({{ site.baseurl }}/assets/img/module1/quidditch-assets/snitch64x64.png)


### 3. Make the `New Game` Button Work

Now we will add some JavaScript to start our game when the user clicks the `new game` button.

For each step below, write your code between the `<script></script>` tags in our index.html file.
* Define a variable, called _score_, and initialize it to 0.
  * We will use this to track the score for our player.

<div class="hint">Hover for hint</div>

{: .hint-content}
```
<script>
  var score = 0;
</script>
```


### Final Solution

<div class="hint">Hover for solution</div>

{: .hint-content}

```
<!DOCTYPE html>
<html>

<head>
	<title>Simple Chat</title>
	<meta charset="utf-8"  />
</head>

<body>
    <!-- The core Firebase JS SDK is always required and must be listed first -->
    <script src="https://www.gstatic.com/firebasejs/8.2.1/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/8.2.1/firebase-firestore.js"></script>

    <h1>Simple Chat</h1>

    <div>Username:</div>
    <input type="text" id="username" placeholder="Rick">
    
    <div>Message:</div>
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

        // Your web app's Firebase configuration
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

        const collectionRef = firestore.collection('messages')

        // Inputs
        const inputUsername = document.getElementById("username")
        const inputMessage = document.getElementById("message")
        const sendButton = document.getElementById("send")

        // Output DIV
        const messagesContainer = document.getElementById("messagesContainer")


        // Add an event listener to add a new message to firestore at our docRef ('chat/general')
        sendButton.addEventListener("click", function() {
                const username = inputUsername.value;
                const textToSave = inputMessage.value;

                collectionRef.add({
                    username: username,
                    txt: textToSave,
                    timestamp: Date.now()
                }).then(function() {
                    console.log("Message Saved!");
                }).catch(function(error){
                    console.log("Got and error:", error);
                });
            })

        // Define a function to listen for real-time updates
        getRealTimeUpdates = function() {
            
            // All documents in our collection, messages, ordered from oldest to newest
            collectionQuery = firestore.collection('messages').orderBy('timestamp', 'asc')

            collectionQuery.onSnapshot(function (snapshot) {
                console.log(snapshot)
                
                // Each snapshot contains one or more DocumentChange objects
                // Loop through each document change
                snapshot.docChanges().forEach( function(docChange) {

                    // Log the document change we detected
                    console.log(docChange)

                    // get the data for this document
                    var data = docChange.doc.data()

                    // Optional:
                    //   docSnapshotChange.type tells us the type of change: 'added', 'modified', 'removed'
                    // console.log(docSnapshotChange.type, message)
                    
                    // Create a new div with this username and message as the content.
                    var div = document.createElement("DIV");   // Create a new <div> element
                    div.innerHTML = data.username + ": " + data.txt; // Insert text for our username and message
                    
                    // Optional: 
                    //   Set the id of our DIV equal to the unique ID of the docuument in our collection.  
                    //   This would come in handy if we needed to remove this DIV from the DOM because the chat message was deleted.
                    // div.id = docChange.doc.id 

                    // Append our div as a child element in our messageContainer div.
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



