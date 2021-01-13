---
layout: default
---


# Practice Problem: Is a hotdog a sandwich?

## Goal

Our goal for this project is to build a website that answers the age old question; is a hotdog a sandwich?

At the end of this activity, you will have built something similar to this:

![best example]({{ site.baseurl }}/assets/img/module3/hotdog_example.png)

## Overview

This activity will allow you to practice using Google Firestore.  You will:
- Learn how to query data on demand.
- Learn how to listen for real-time updates to the data in the database.
- Change the DOM to reflect the hot dog status stored in our database.

## Instructions

#### Starter Code
First things first, you need to create a new folder called 'hotdog' and place an index.html file into it.  Use the starter HTML code provided below to jump start you.

```
<!DOCTYPE html>
<html>
    <head>
        <title>Hot dogs == sandwiches?</title>
        <script src="https://www.gstatic.com/firebasejs/8.2.1/firebase-app.js"></script>
        <script src="https://www.gstatic.com/firebasejs/8.2.1/firebase-firestore.js"></script>
    </head>
    <body>
        <h1 id="hotDogOutput">Hot dog status:</h1>
        <input type="textfield" id="latestHotDogStatus"/>
        <button id="saveButton">Save</button>

        <!--Unlike the video tutorial, we are keeping all our javascript inline in our html file.-->
        <script>

            // Replace with your web app's Firebase configuration
            var firebaseConfig = {
                apiKey: "...",
                authDomain: "...",
                projectId: "...",
                storageBucket: "...",
                messagingSenderId: "..."",
                appId: "..."
            };

            // Initialize our application
            firebase.initializeApp(firebaseConfig);
            var firestore = firebase.firestore();

            const docRef = firestore.doc("sample/sandwichdata")
            const outputHandler = document.getElementById("hotDogOutput")
            const inputTextField = document.getElementById("latestHotDogStatus")
            const saveButton = document.getElementById("saveButton")
        </script>
    </body>
</html>
```

#### Video Tutorial
Following along, step by step, with this Video Tutorial.  Heads up, there is one point in the video where he talks about security rules, you can consider this part optional as we disabled security when we created our database earlier.  Obviously, in a more serious application we would want to spend time securing our database.

<iframe width="560" height="315" src="https://www.youtube.com/embed/2Vf1D-rUMwE" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### Conclusion

After following the video tutorial you should have the completed application.  See below for the complete solution.

<div class="hint">Hover for Final Solution</div>

{: .hint-content}

```
<!DOCTYPE html>
<html>
    <head>
        <title>Hot dogs == sandwiches?</title>
        <script src="https://www.gstatic.com/firebasejs/8.2.1/firebase-app.js"></script>
        <script src="https://www.gstatic.com/firebasejs/8.2.1/firebase-firestore.js"></script>
    </head>
    <body>
        <h1 id="hotDogOutput">Hot dog status:</h1>
        <input type="textfield" id="latestHotDogStatus"/>
        <button id="saveButton">Save</button>
        <button id="loadButton">Load</button>

        <!--Unlike the video tutorial, we are keeping all our javascript inline in our html file.-->
        <script>

            // Replace with your web app's Firebase configuration
            var firebaseConfig = {
                apiKey: "...",
                authDomain: "...",
                projectId: "...",
                storageBucket: "...",
                messagingSenderId: "..."",
                appId: "..."
            };

            // Initialize our application
            firebase.initializeApp(firebaseConfig);
            var firestore = firebase.firestore();

            const docRef = firestore.doc("sample/sandwichdata")
            const outputHandler = document.getElementById("hotDogOutput")
            const inputTextField = document.getElementById("latestHotDogStatus")
            const saveButton = document.getElementById("saveButton")
            const loadButton = document.getElementById("loadButton")

            saveButton.addEventListener("click", function() {
                const textToSave = inputTextField.value;

                docRef.set({
                    hotDogStatus: textToSave
                }).then(function() {
                    console.log("Status Saved!");
                }).catch(function(error){
                    console.log("Got and error:", error);
                });
            })

            loadButton.addEventListener("click", function() {
                docRef.get().then(function (doc) {
                    if(doc && doc.data) {
                        const myData = doc.data();
                        outputHandler.innerText = "Hot Dog status: " + myData.hotDogStatus;
                    }
                }).catch(function (error) {
                    console.log("Got an error:", error)
                });
            });

            getRealTimeUpdates = function() {
                docRef.onSnapshot(function (doc) {
                    if(doc && doc.data) {
                        const myData = doc.data();
                        outputHandler.innerText = "Hot Dog status: " + myData.hotDogStatus;
                    }
                });
            }

            getRealTimeUpdates();
            
        </script>
    </body>
</html>
```

If your mind is still blown, no worries.  We will review this entire solution in the live session.
<iframe src="https://giphy.com/embed/xT0xeJpnrWC4XWblEk" width="480" height="320" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/whoa-hd-tim-and-eric-xT0xeJpnrWC4XWblEk">via GIPHY</a></p>