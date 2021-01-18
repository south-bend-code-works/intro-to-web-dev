<!--

Agenda:
0. House Keeping: Cover any issues / concerns for the course.
1. Databases in general
  - store data
  - not unfamiliar with them even if we haven't used one ourselves
  - Relational 
    - excel sheets of student, classes analogy
  - Document Store
    - use this at work with new clients
    - i can set up rules (is_deleted)
2. Firestore
  - explain Firebase vs Firestore
    - Firebase is a Google product that has lots of features
    - Firestore is a feature
    - Old firebase database
      {
        favoriteNum: 2,
        users: {
          user1: {
            name: 'Joshua',
            occupation: 'Web dev',
          },
          user2: {
            name: 'David',
            occupation: 'Wizard',
          }
        },
        favoriteBook: 'A Cactus: Who they are and where they are going',
      }
    - New Firestore
2.5 Review a Promise

      var roomIsClean = true

      var promiseToCleanRoom = () => {
        return new Promise((resolve, reject) => {

          if (roomIsClean) {
            resolve("Good work!")
          } else {
            reject("Room isn't clean yet...")
          }

        })
      }
      
      promiseToCleanRoom()
        .then((val) => {
          console.log(val)
        })
        .catch((val) => {
          console.log(val)
        })

3. Create a new project in Firebase
  - go slowly and allow for questions
4. Copy and Paste Hot Dog app and go over it


-->


<!DOCTYPE html>
<html>

    <head>
        <title>Hot dogs == sandwich?</title>
        <script src="https://www.gstatic.com/firebasejs/8.2.1/firebase-app.js"></script>
        <script src="https://www.gstatic.com/firebasejs/8.2.1/firebase-firestore.js"></script>
    </head>

    <body>
        <h1 id="output">Hot dog status:</h1>
        <input type="textfield" id="latestHotDogStatus"/>
        <button onclick="saveData()">Save</button>
        <button onclick="loadData()">Load</button>

        <!--Unlike the video tutorial, we are keeping all our javascript inline in our html file.-->
        <script>

            // Replace with your web app's Firebase configuration
            var firebaseConfig = {
              apiKey: "AIzaSyCbWywXfRnEPk68ggckBtZU6JjsviOFss0",
              authDomain: "mister-test-boi.firebaseapp.com",
              projectId: "mister-test-boi",
              storageBucket: "mister-test-boi.appspot.com",
              messagingSenderId: "152243657922",
              appId: "1:152243657922:web:d4a264d522912764f42f5b"
            };

            // Initialize our application
            firebase.initializeApp(firebaseConfig);
            var firestore = firebase.firestore();

            var docRef = firestore.doc("sample/sandwichdata")

            var outputEle = document.getElementById("output")
            var inputEle = document.getElementById("latestHotDogStatus")


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