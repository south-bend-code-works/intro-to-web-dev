<!--

 _____  ___    ___    _  _     _____  ___   _____     ___    ___    _   _  ___    ___    _____  _____  _____  ___   
(  _  )(  _`\ (  _`\ (_)(_)   (  _  )|  _`\(_   _)   (  _`\ (  _`\ ( ) ( )(  _`\ |  _`\ (  _  )(_   _)(  _  )|  _`\ 
| (_) || (_(_)| ( (_)| || |   | (_) || (_) ) | |     | ( (_)| (_(_)| `\| || (_(_)| (_) )| (_) |  | |  | ( ) || (_) )
|  _  |`\__ \ | |  _ | || |   |  _  || ,  /  | |     | |___ |  _)_ | , ` ||  _)_ | ,  / |  _  |  | |  | | | || ,  / 
| | | |( )_) || (_( )| || |   | | | || |\ \  | |     | (_, )| (_( )| |`\ || (_( )| |\ \ | | | |  | |  | (_) || |\ \ 
(_) (_)`\____)(____/'(_)(_)   (_) (_)(_) (_) (_)     (____/'(____/'(_) (_)(____/'(_) (_)(_) (_)  (_)  (_____)(_) (_)
                                                                                                                    
                                                                                                                    
http://patorjk.com/software/taag/#p=display&f=Puffy&t='Fin

Agenda:
-1. Introduce yourself

0. House Keeping: Review how the class is structured.

1. Review how the web works
    - Class Discussion
    - Show how chrome works
    - Backend / Front End (We are only on Front End for now)
2. HTML / CSS
    - What is HTML
    - Structure of an HTML Document
    - Friend-o-Gram
3. GIT / TERMINAL
4. Hosting your website on github
5. Review Final Project Part 1 (last 5 minutes)

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

4. Participation / Communication (How we will use Zoom)
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

 _   _  _____         _            _        ___    ___    ___   
( ) ( )(_   _)/'\_/`\( )          ( )      (  _`\ (  _`\ (  _`\ 
| |_| |  | |  |     || |        __| |__    | ( (_)| (_(_)| (_(_)
|  _  |  | |  | (_) || |  _    (__   __)   | |  _ `\__ \ `\__ \ 
| | | |  | |  | | | || |_( )      | |      | (_( )( )_) |( )_) |
(_) (_)  (_)  (_) (_)(____/'      (_)      (____/'`\____)`\____)
                                                                
                                                                
1. Now we are going to code together.  
2. Open Visual Studio Code.
3. Brief review of VsCode
4. Build Friend-o-gram together from scratch
-->

<!-- Build the skeleton HTML structure
1. Discuss each part of this structure with the class, ask lots of questions
    - Example: Why is <head> important? <-- this is great!>
    - Why do we open and close our tags?
    - Run this in your browser - why don't we see anything?
    - Compare this to the craigslist example

    - Discuss some vscode features (type ahead, syntax color, etc)

    Use basic HTML tags:
        <h1>
        <p>
-->
```html
<!DOCTYPE html>
<html>
  <head>
    <style>
    </style>
  </head>
  <body>
    <!-- Have the students add a title to the page using the header tags-->
    <h1>Friend-o-gram</h1>

    <!-- Have the students add a description to the page using the p tags-->
    <p>These are my friends<p>
  </body>
</html>
```

<!-- Host our page on github 
 ___       _    _   _         _     
(  _`\  _ ( )_ ( ) ( )       ( )    
| ( (_)(_)| ,_)| |_| | _   _ | |_   
| |___ | || |  |  _  |( ) ( )| '_`\ 
| (_, )| || |_ | | | || (_) || |_) )
(____/'(_)`\__)(_) (_)`\___/'(_,__/

0. Quickly Describe what github is in your own words
    - mention it's free
    - the nature of open source and software
1. Open the command line 
    - Mac People: Use Terminal
    - Windows People: Use Git Bash
2. Use "cd" to navigate to your directory
3. git init
4. git add index.html
5. git commit -m "Initial Commit"
6. You have created your local git repo, let's host it in GitHub
7. Go to GitHub.com, create a new project called friend-o-gram
8. Follow the instructions for "or push an existing repository from the command line"
    1. git remote add origin https://github.com/<your username>/<your repo name>.git
    2. git branch -M main
    3. git push -u origin main
9. congrats/WOW/Cool/Nice - Refresh the repo to see that your files are there!   
10.  Host it on github pages (talk about servers again) 
    1. Settings->GitHub Pages, select main branch (use root)
    2. Your site is published! 
    3. https://<username>.github.io/<reponame>/
11.  Note the custom domain field, if you want to buy yourname.com you can connect it up!
-->


<!-- Fully build out friend-o-gram

 ___                              _                                                   
(  _`\       _                   ( )                                                  
| (_(_)_ __ (_)   __    ___     _| | ______   _   ______   __   _ __   _ _   ___ ___  
|  _) ( '__)| | /'__`\/' _ `\ /'_` |(______)/'_`\(______)/'_ `\( '__)/'_` )/' _ ` _ `\
| |   | |   | |(  ___/| ( ) |( (_| |       ( (_) )      ( (_) || |  ( (_| || ( ) ( ) |
(_)   (_)   (_)`\____)(_) (_)`\__,_)       `\___/'      `\__  |(_)  `\__,_)(_) (_) (_)
                                                        ( )_) |                       
                                                         \___/'                       

2. Teach DIVs, class, id, img tag

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
    <!-- Have the students add a title to the page using the header tags-->
    <h1>Friend-o-gram</h1> 

    <!-- Have the students add a description to the page using the p tags-->
    <p>These are my friends<p>
    
    <!-- There are several ways to build our grid of photos.-->

    <!--Way 1: With classes-->
    <h2>Div with classes</h2>
    <div class="photo-wrapper"> <!--Talk about the nested divs and how this works-->
      <div class="photo" id="photo-1">Photo 1 here</div>
      <div class="photo" id="photo-2">Photo 2 here</div>
      <div class="photo" id="photo-3">Photo 3 here</div>
      <div class="photo" id="photo-4">Photo 4 here</div>
      <div class="photo" id="photo-5">Photo 5 here</div>
      <div class="photo" id="photo-6">Photo 6 here</div>
    </div>

    <!-- Way 2: Without using classes -->
    <h2>Without classes on the individual photos</h2>
    <div class="photo-wrapper">
      <div id="photo-1">Photo 1 here</div>
      <div id="photo-2">Photo 2 here</div>
      <div id="photo-3">Photo 3 here</div>
      <div id="photo-4">Photo 4 here</div>
      <div id="photo-5">Photo 5 here</div>
      <div id="photo-6">Photo 6 here</div>
    </div>

    <!-- Way 3: Using img tags -->
    <h2>Using img tags</h2>
    <div class="photo-wrapper">
      <img src="photo-1.jpg">
      <img src="photo-2.jpg">
      <img src="photo-3.jpg">
      <img src="photo-4.jpg">
      <img src="photo-5.jpg">
      <img src="photo-6.jpg">
    </div>
  </body>
</html>
```


<!-- Update your project on github - You can do this throughout the class at key milestones.  
 _   _  ___    ___    _____  _____  ___       ___    _  _____  _   _  _   _  ___   
( ) ( )(  _`\ (  _`\ (  _  )(_   _)(  _`\    (  _`\ (_)(_   _)( ) ( )( ) ( )(  _`\ 
| | | || |_) )| | ) || (_) |  | |  | (_(_)   | ( (_)| |  | |  | |_| || | | || (_) )
| | | || ,__/'| | | )|  _  |  | |  |  _)_    | |___ | |  | |  |  _  || | | ||  _ <'
| (_) || |    | |_) || | | |  | |  | (_( )   | (_, )| |  | |  | | | || (_) || (_) )
(_____)(_)    (____/'(_) (_)  (_)  (____/'   (____/'(_)  (_)  (_) (_)(_____)(____/'
                                                                                   
                                                                                                                                                     
1. git add -A
2. git commit -m "message"
3. git push
4. Go to github.com / your github site and refresh.


<!-- 
 ___    _  _   _  _____  _         ___    _    _  _____         ___    _      ___   
(  _`\ (_)( ) ( )(  _  )( )       (  _`\ ( )  ( )(  _  )/'\_/`\(  _`\ ( )    (  _`\ 
| (_(_)| || `\| || (_) || |       | (_(_)`\`\/'/'| (_) ||     || |_) )| |    | (_(_)
|  _)  | || , ` ||  _  || |  _    |  _)_   >  <  |  _  || (_) || ,__/'| |  _ |  _)_ 
| |    | || |`\ || | | || |_( )   | (_( ) /'/\`\ | | | || | | || |    | |_( )| (_( )
(_)    (_)(_) (_)(_) (_)(____/'   (____/'(_)  (_)(_) (_)(_) (_)(_)    (____/'(____/'
                                                                                    
                                                                                    
EXAMPLE of fully build out friend-o-gram -->
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
        /* Every photo should have a background-image, but different size/shape photos may need other attributes */
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