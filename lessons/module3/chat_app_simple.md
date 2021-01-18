---
layout: default
---

# Project Part 1: Simple Chat App

## Goal

The objective for this project is to build a simple web-based chat app that allows two or more people to chat.  At the end of this activity, we will have built something similar to the screenshot below.

![chat example]({{ site.baseurl }}/assets/img/module2/simple-chat-1.0-animated.gif)

### Project Requirements

You will need to open your website in two or more different web browser tabs to simulate different users chatting with one another.

1. User 1 types a message, it is displayed on their screen and it is saved into Firestore.
2. User 2 sees the message from User 1 appear on their screen without needing to refresh the page.
3. User 2 types a response, it is displayed on the screen below User 1's message and is saved to Firestore
4. User 1 sees the message from User 2 appear on the screen without needing to refresh the page.


#### Data Structure
Your Firestore database will have one collection, called `messages`.  Each chat message sent will be added as a new document to this collection.

Each document should, at a minimum, contain the following 3 fields:
1. `username`: the handle for the user who sent the message
2. `txt`: the message the user wants to send
3. `timestamp`: the time when the message was sent (get it by calling `Date.now()`)

#### Starter Code

1. Create a a folder called chat-app and save the following code in a index.html file.
2. Replace the `...` values in the starter code's firebaseConfig object with the values from your Firestore project.  You can find these values in your Firestore project settings tab in the [firebase console](https://console.firebase.google.com/).
3. You'll also need to ensure that the version numbers (e.g. 8.2.1) for your Firebase JS SDK match what you see in your Firestore project settings.
 
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

    <h1>Simple Chat</h1>

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
      var firestore = firebase.firestore();
    </script>
</body>
</html>
```

#### Try it out
* Open your page in Chrome.
* You'll see the text input boxes and the button for our app, but nothing will work yet!

### Think through the steps for your application

<p>First, Let's pause and think through, at a high level, the steps that need to happen to send and receive a message.</p>

1. The user types a message and presses the send button.
2. The message, username, and timestamp is saved as a new document in our `messages` collection in Firestore.
3. Firestore will then generate a real-time update event to alert any applications listening that a new document was added.
4. Both User 1 and User 2's web application will receive the real-time update, parses the message, and adds a new `div` to the DOM with the message txt.


### Wire-up our send button

1. Add a new variable, `sendButton` to our javascript.  It should be set equal to the element with ID of `send`. 
2. Wire up an event listener to our send button to respond to "clicks".  Recall that addEventListener take a function as the second argument.  For now, let's simply have that function log to the console that the button was clicked.

<div class="hint">Hover for hint</div>

{: .hint-content}

```

        // Inputs
        var inputUsername = document.getElementById("username")
        var inputMessage = document.getElementById("message")
        var sendButton = document.getElementById("send")

        // 
        sendButton.addEventListener("click", function() {
                console.log("the button was clicked");
            })
```

Good job, now test your button and make sure you see the text in your web browsers console.  It's very helpful when coding to make small incremental steps like this as it makes it easier to debug!

### Save our data to firestore

Now that our button works, we are ready to save our chat message to the database.  Recall the chat message should have a username, txt, and datetime.

Recall that in Firestore is a document database and we need one collection of documents, called `messages`.  In order to use this collection, we first  need to ask Firestore for a reference to this collection.  Add the following code to your JavaScript to get our collection reference.  Put this code just after the code that initializes our application.

```
var collectionRef = firestore.collection('messages')
```

Awesome, now let's add documents to our collection.  This is done by calling the `collectionRef.add()`.  This function takes one argument, which is the javascript object want save.  A sample message is provided below.  Of course, in your code you will not want to hard-code the username and txt.  You'll need to get that by getting the value of the `inputUsername` and `inputMessage`

```
var msgObj = {
    username: "Rick",
    txt: "Hi Morty",
    timestamp: Date.now()
}

collectionRef.add(msgObj)
```

A quick aside about collectionRef.add and `promises`.  When we call collectionRef.add() we are asking a remote server to save some data to the database.  This might take a few seconds, which is why collectionRef.add() is an asynchronous function call that returns a javascript `promise`.  Simply put, we are  asking the database to promise to let us know when it's done doing it's thing.  Therefore, once the promise is fulfilled, we can use .then() to take an action, such as log that the message was saved succesfully.  Similarly, if the database goes off and tries to add the data for a few seconds and fails, we can use the .catch() method to handle that error.  See the code below for some example syntax.

```
collectionRef.add(msgObj).then(function() {
                    console.log("Message Saved!");
                }).catch(function(error){
                    console.log("Got and error:", error);
                })
```

Finally, you have what you need to update your sendButton's eventListener.  Replace our console.log call from wireing up our send button with the code you wrote to save our message to Firestore.

<div class="hint">Hover for hint</div>

{: .hint-content}

```
<script>

        // ---------------------------------------
        // Initialize Firebase and Firestore
        // ---------------------------------------

        // Your web app's Firebase configuration
        var firebaseConfig = {
          apiKey: ...,
          authDomain: ...,
          projectId: ...,
          storageBucket: ...,
          messagingSenderId: ...,
          appId: ...
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


        // Add an event listener to our button that adds a new message to our firestore collection
        sendButton.addEventListener("click", function() {
                var username = inputUsername.value;
                var textToSave = inputMessage.value;

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
      </script>
```

#### Try it out
* Reload your updated `index.html` in your browser.
* Type in a user name and a message and click "send".
* In another tab, open your firebase console and click on Firestore.
* You should see a new collection, called 'messages', with one or more documents that reflect your messages!

Sadly, no messages will be displayed on our webpage yet.  That is because we still have to tell our html page code to listen for new messages and to display them on the screen.

### Listen for Real-time updates from Firestore

In order to get the chat messages to display on anyone using our website, we need our code to listen for any real-time changes that occur in our collection.  In short, we want to be alerted any-time a document is added to our collection so we can display that message on the screen.

To do this, we will follow the same pattern that we did with the hot-dog app, with one major exception.  In the hot dog app we were listening for changes to a single document.  In this case, we are going to listen to changes for the entire collection.

First, we need to define a function to call to start listening to real-time updates:

```
// Define a function to listen for real-time updates
var getRealTimeUpdates = function() {
  // Our code here
}
```

The getRealTimeUpdates function needs a reference to the entire collection so that we can listen for updates.  Interestingly, because we Firestore does not guarantee the order of the documents in the collection, we also need to `order` our documents from the newest document to the oldest so our chat messages don't get jumbled up.

```
collectionQuery = firestore.collection('messages').orderBy('timestamp', 'asc')
```

Once we have the reference to our collection, we will use onSnapshot() to listen to real-time changes.

```
collectionQuery.onSnapshot(function (snapshot) {
  // Do something with our snapshot
  console.log(snapshot)
}
```

Pause and update your application.  What do you see in the console.log()?

You may have noticed that each snapshot contains one or more DocumentChange objects.  We are going to want to process all document changes we recieve, which means we need to loop through each change.

```
  // Loop through each document change
  snapshot.docChanges().forEach( function(docChange) {
    // Do something with this document Change
    console.log(docChange)
  }
```

We can access the data inside each docChange object by calling the data() function on the change's doc reference.
```
// get the data for this document
var data = docChange.doc.data()

console.log(data.username, data.txt)
```

Now that we have the username and message text, we need to display the message to in our HTML by appending a new `<DIV>` to our messageContainer.

```
 // Create a new div with this username and message as the content.
  var div = document.createElement("DIV");   // Create a new <div> element
  div.innerHTML = data.username + ": " + data.txt; // Insert text for our username and message
  
  // Append our div as a child element in our messageContainer div.
  messagesContainer.appendChild(div); 
```

That is about it!  Now your application is listening and responding to real-time updates from Firestore.

### Try it out

Once you have put everything together, you now should have an application that can save messages, read messages, and display them on your webpage.  If you are stuck, feel free to reference the final solution below.  We will go over this in detail in the live session in case you have any questions.

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

        var collectionRef = firestore.collection('messages')

        // Inputs
        var inputUsername = document.getElementById("username")
        var inputMessage = document.getElementById("message")
        var sendButton = document.getElementById("send")

        // Output DIV
        var messagesContainer = document.getElementById("messagesContainer")


        // Add an event listener to our button that adds a new message to our firestore collection
        sendButton.addEventListener("click", function() {
                var username = inputUsername.value;
                var textToSave = inputMessage.value;

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
        var getRealTimeUpdates = function() {
            
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