---
layout: default
---
# Overview 

## Agenda
0. House Keeping: Cover any issues / concerns for the course.
1. What is a Database?
2. How to navigate firebase console
3. Review the HotDog app
5. Questions about simple chat

## Zoom Links

### Section 1 (10am to 12pm)
<https://notredame.zoom.us/j/96545079849?pwd=K3psL1J4Q3FUNmxCbmpSa0pTbm9ndz09>

**Meeting ID: 965 4507 9849**

**Passcode: 835805**


### Section 2 (1pm to 3pm) 
<https://notredame.zoom.us/j/99670056329?pwd=OXRmSFNERU45Vi9ndkpJNUpGTFU1QT09>

**Meeting ID: 996 7005 6329**

**Passcode: 781595**

### Section 3 (4pm to 6pm) 
<https://notredame.zoom.us/j/92241686868?pwd=aHBiTmdOM25Eak52UEtOQU5XeDJvZz09>

**Meeting ID: 922 4168 6868**

**Passcode: 122449**

## Solution From Session 1
```
<!DOCTYPE html>
<html>

    <head>
        <title>Hot dogs == witches?</title>
        <script src="https://www.gstatic.com/firebasejs/8.2.1/firebase-app.js"></script>
        <script src="https://www.gstatic.com/firebasejs/8.2.1/firebase-firestore.js"></script>
    </head>

    <body>
        <h1 id="output">Hot dog status:</h1>
        <input id="input"/>
        <button onclick="saveData()">Save</button>
        <button onclick="loadData()">Load</button>

        <!--Unlike the video tutorial, we are keeping all our javascript inline in our html file.-->
        <script>

            // Replace with your web app's Firebase configuration
            var firebaseConfig = {
              apiKey: "AIzaSyCUIjfgCLd7WK3WULetVhcmS40iR0KVUbs",
              authDomain: "nd-bc-session-1.firebaseapp.com",
              projectId: "nd-bc-session-1",
              storageBucket: "nd-bc-session-1.appspot.com",
              messagingSenderId: "717477573552",
              appId: "1:717477573552:web:2c924a7e2cb117f93edc75"
            }

            // Initialize our application
            firebase.initializeApp(firebaseConfig)
            var firestore = firebase.firestore()

            var docRef = firestore.doc("sample/sandwichdata")

            var outputEle = document.getElementById("output")
            var inputEle = document.getElementById("input")


            var saveData = () => {
              var textToSave = inputEle.value

              var dataToSave = {
                hotDogStatus: textToSave,
              }
              docRef.set(dataToSave)
            }


            var loadData = () => {

              docRef.get().then((doc) => {
                var myData = doc.data()
                if (myData !== undefined) {
                  outputEle.innerHTML = "Hot dog status: " + myData.hotDogStatus
                }
              })

            }

            var getRealTimeUpdates = () => {

              docRef.onSnapshot((doc) => {
                var myData = doc.data()
                if (myData !== undefined) {
                  outputEle.innerHTML = "Hot dog status: " + myData.hotDogStatus
                }
              })
              
            }

            getRealTimeUpdates()
            
        </script>
    </body>
</html>
```