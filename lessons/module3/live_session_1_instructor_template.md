<!--

Agenda:
0. House Keeping: Cover any issues / concerns for the course.
0.5. Please ask questions
  - I know it is review but please ask questions
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

3. Create a new project in Firebase
  - go slowly and allow for questions
4. Copy and Paste Hot Dog app and go over it
4.5 Review a Promise

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


-->
<!DOCTYPE html>
<html>

    <head>
    </head>

    <body>
    </body>

    <script>

      var roomIsClean = true

      // some function that reaches out to another server and then returns data

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
        .then((data) => {
          console.log("Good:", data)
        })
        .catch((err) => {
          console.log("Bad:", err)
        })
        

    </script>
</html>

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
              apiKey: "AIzaSyBAjYoc_aZF5Dl_cyftLw87-Cr7qTvzyR0",
              authDomain: "nd-bc-session-2.firebaseapp.com",
              projectId: "nd-bc-session-2",
              storageBucket: "nd-bc-session-2.appspot.com",
              messagingSenderId: "528200283037",
              appId: "1:528200283037:web:607db3bc977fe5f05db574"
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

              docRef.get()
                .then((doc) => {
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