---
layout: default
---

# Setup Firestore
At this point you must be thinking, it would be awesome if I had my very own database! You are right, having a database does make you cool. Lucky for us, Google has built Firestore; a flexible, scaleable, and cloud based database that you can start using for free.

## Goal
By the end of this lesson, you will have:

1. Created a Firebase Project
2. Created a Firestore Database
3. Created a web application for your firestore database


### Setup Firestore
#### 1. Create your Firebase project
Your Firebase project will contain your Firestore database.

1. Go to [https://console.firebase.google.com/u/0/?pli=1](https://console.firebase.google.com/u/0/?pli=1)
2. Click Create Project (or Add Project)
3. Give your project a name, for example: intro-to-webdev-chat-app
4. Disable Google Analytics (we don’t need this yet)
5. Click “Create Project”
6. After a few moments, your project will be created and will look something like this:

![firebase project example]({{ site.baseurl }}/assets/img/module2/firebase-1.png)

#### 2. Create your Firestore database 
Now it's time to actually create your Firestore Database.  Firestore is one of many of things you can setup in a Google Firebase projects, for now, you can pretty much ignore everything else.

1. Go to [https://console.firebase.google.com/u/0/?pli=1](https://console.firebase.google.com/u/0/?pli=1)
2. Click on “Cloud Firestore” in the left hand menu
4. Click “Create Database”
5. Click “Start in Test Mode”, then Next
    1. This creates your database without any user based security, which is fine while we are just getting started.  In 30 days, Firebase will automatically set your data to be private.
6. Set your Cloud Firestore Location to us-central, this is simply where the server is in the world.  Servers closer to your users will be faster!
7. After a few moments your cloud firestore database will be provisioned!  
8. You should see a screen that would show your data eventually.  We don't have any yet, so it's pretty boring, but it will look like this:

![firebase project example]({{ site.baseurl }}/assets/img/module2/firebase-2.png)

#### 3. Create your Firestore Web Application 
You have to register your web application with your Firestore database.  Doing this gives you an apiKey.  The apiKey which just identifies your Firebase project on the Google servers. It also gives you an appKey, which identifies this web application.  It is not a security risk for someone to know these keys. In fact, it is necessary for them to know it, in order for them to interact with your Firebase project. 

1. Go to [https://console.firebase.google.com/u/0/?pli=1](https://console.firebase.google.com/u/0/?pli=1)
2. In the left hand side, click on the gear icon next to “Project Overview” to bring up your project's settings.
3. Scroll down and under `Your Apps`, click on the icon to create a Web App.
4. Give your app a name and press "Register App"
4. You will see some code we need to add to our web application.  It contains:
    1. The first part is the code that includes the firebase library so that we can use the database.
    2. The second part contains an object called firebaseConfig, which contains attributes for our apiKey, appKey, and others.
    3. A line of code to connect our app to our database: `firebase.initializeApp(firebaseConfig);`

![firebase project example]({{ site.baseurl }}/assets/img/module2/firebase-3.png)

### Conclusion
BOOM, you've completed all of the steps to setup your first Firestore database in the cloud.  Next, you will watch a couple of short video tutorials to help bring you up to speed on Firestore.

<iframe src="https://giphy.com/embed/xT9Iggof3MKS2LonOo" width="480" height="258" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/chozynboy-walking-explosion-xT9Iggof3MKS2LonOo">via GIPHY</a></p>
