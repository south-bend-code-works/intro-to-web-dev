<!--


Agenda:
-1. Introduce yourself 

0. House Keeping: Review how the class is structured.

0.5. How to use Vim

1. Review how the web works
    - Class Discussion
    - Show how chrome works
    - Backend / Front End (We are only on Front End for now)
2. HTML
    - What is HTML
    - Structure of an HTML Document
    - Friend-o-Gram
3. CSS
4. How to use command line (terminal / git bash - (ls, cd, mkdir - file paths) + git)
5. How to use git
6. Launching your repo on github Pages
 
-->

<!-- House Keeping (25 minutes)
| | | |                    | |                 (_)            
| |_| | ___  _   _ ___  ___| | _____  ___ _ __  _ _ __   __ _ 
|  _  |/ _ \| | | / __|/ _ \ |/ / _ \/ _ \ '_ \| | '_ \ / _` |
| | | | (_) | |_| \__ \  __/   <  __/  __/ |_) | | | | | (_| |
\_| |_/\___/ \__,_|___/\___|_|\_\___|\___| .__/|_|_| |_|\__, |
                                         | |             __/ |
                                         |_|            |___/

1. Review the course structure (each week we will...)
   - ITS CRITICAL THAT YOU DO THE PRE-WORK.  
   - IN THE LIVE SESSION YOU WILL BE EXPECTED TO BE FAMILIAR WITH THE MATERIAL.  
   - THE LIVE SESSIONS BUILD ON THE PRE-WORK PRACTICE PROBLEM.

   ---- Pattern for the Course
   - Pre-Work
   - Practice Problem
   - Live Session
   - Final Project for the week

2. Feedback
    - NO GRADES
    - Feedback is critical to learning, so your work will still be reviewed.
        - Instructor Review in the live sessions
        - Peer Review in the Labs as well as in the live sessions (in a limited way)
    - You are not submitting any work in the traditional way, however, you are sharing all of your work on GitHub (lead in to #3)

3. Portfolio of Work
    - The biggest outcome is that you will produce a portfolio of work, published in GitHub.
        - For Example, at the end of the first week you will have 3 projects published (Friend-o-Gram, Quidditch, Virtual Pet)
    - The projects are important, but it's also important to show your code (recruiters, potential employers)

3. Participation / Communication (How we will use Zoom)
    - I want you to talk in the live session.
    - At any time, you can unmute your microphone and ask a question.
    - I am also monitoring the chat, and I will answer any questions you post their as well.
    - Please use the chat in zoom for the live session.
    - Asking questions outside of class
        1. Use the weekly slack channel (show them slack at this point)
            - Posting your question in slack is best as you are likely not the only student with the question.
            - Get answers faster: I will answer questions in slack before answering them in email.
        2. You can still send me an email, I will answer, but it may be delayed a bit.
-->

<!--How the Web Works (5 -10 minutes)

1. Discussion: 
    Recall the video that you watched.  What surprised you about how the web works?
    - Wow, what great answers!
    - Get them to explain to you servers and clients (backend - front end)
        - Servers host HTML files
        - Browsers request and render HTML files
2. How Chrome Works
 _____ _
/  __ \ |                             
| /  \/ |__  _ __ ___  _ __ ___   ___ 
| |   | '_ \| '__/ _ \| '_ ` _ \ / _ \
| \__/\ | | | | | (_) | | | | | |  __/
 \____/_| |_|_|  \___/|_| |_| |_|\___|
    - Show going to www.craigslist.com. Click "View Source"
    - Explain that the code is running in your browser
    - Open Chrome dev tooling + inspect element
    - change a headline to something funny
    - explain that you are not changing the website for everyone, but just for your current browser
    - show refreshing the page and that the changes you made disappear

-->

<!-- Recap on HTML
 _   _ ________  ___ _    
| | | |_   _|  \/  || |    
| |_| | | | | .  . || |    
|  _  | | | | |\/| || |    
| | | | | | | |  | || |____
\_| |_/ \_/ \_|  |_/\_____/

1. Now we are going to code together.  
2. Open Visual Studio Code.
3. Brief review of VsCode
4. Build Friend-o-gram together from scratch
-->

<!-- Build the skeleton
1. Discuss each part of this structure with the class, ask lots of questions
    - Example: Why is <head> important? <-- this is great!>
    - Why do we open and close our tags?
    - Run this in your browser
    - Compare this to the craigslist example

    - Discuss some vscode features (type ahead, syntax color, etc)
-->
```html
<!DOCTYPE html>
<html>
  <head>
    <style>
    </style>
  </head>
  <body>
  </body>
</html>
```


<!--
2. Fill out the body with our content.

Review basic HTML tags:
<h1>
<p>
<ul><ol> <li>
<div>

Use inspect element to review the structure and talk about.
-->
```html
<!DOCTYPE html>
<html>
  <head>
    <style>
    </style>
  </head>
  <body>
    <h1>Friend-o-gram</h1>
    <p>These are my friends<p>
    <div>Photo 1 here</div>
    <div>Photo 2 here</div>
    <div>Photo 3 here</div>
    <div>Photo 4 here</div>
    <div>Photo 5 here</div>
    <div>Photo 6 here</div>
  </body>
</html>
```

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        display: grid;
        grid-template-columns: auto auto auto;
      }
      p {
          color: red;
      }
      .photo {
        height: 400px;
        background-size: cover;
        background-position: 50% 50%;
      }
      #photo-1 {
        background-image: url('photo-1.jpg');
        background-position: 50% 0%;
      }
      #photo-2 {
        background-image: url('photo-2.jpg');
      }
      #photo-3 {
        background-image: url('photo-3.jpg');
      }
      #photo-4 {
        background-image: url('photo-4.jpg');
      }
      #photo-5 {
        background-image: url('photo-5.jpg');
      }
      #photo-6 {
        background-image: url('photo-6.jpg');
      }
    </style>
  </head>
  <body>
    <div class="photo" id="photo-1"></div>
    <div class="photo" id="photo-2"></div>
    <div class="photo" id="photo-3"></div>
    <div class="photo" id="photo-4"></div>
    <div class="photo" id="photo-5"></div>
    <div class="photo" id="photo-6"></div>
  </body>
</html>
```