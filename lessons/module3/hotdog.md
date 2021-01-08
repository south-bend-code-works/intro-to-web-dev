---
layout: default
---


# Is a hotdog a sandwich?

## Goal

Our goal for this project is to build a delicious, website that answers the age old question; is a hotdog a sandwich?

At the end of this activity, you will have built something similar to this:

![best example]({{ site.baseurl }}/assets/img/module3/hotdog_example.png)

## Overview

This activity will allow you to practice using Google Firestore.  You will:
- Learn how to query data on demand.
- Learn how to listen for real-time updates to the data in the database.
- Change the DOM to reflect the value stored in our database.

## Instruction

We are going to create a very simple website that answers the eternal question, is a hotdog a sandwich?

#### Starter Code
First things first, you need to create a new folder called 'hotdog' and place an index.html file into it.  You can use the basic HTML code provided below to jump start you.

```
<!DOCTYPE html>
<html>
    <head>
        <title>Is a hot dog a sandwich?</title>
        <meta charset="utf-8" />
        <style>
            #answer {
                color:red
            }
        </style>
    </head>
    <body>
        <h1>Is a hot dog a sandwich? </h1> <h1 id="answer">Yes</h1>
        <button onclick="changeAnswer()">Change Answer</button>

        <script>
            function changeAnswer() {
                answer = document.getElementById("answer").innerHTML
                if(answer == "No") {
                    document.getElementById("answer").innerHTML = 'Yes'
                } else {
                    document.getElementById("answer").innerHTML = 'No'
                }
            }
        </script>
    </body>
</html>
```

#### Try it out
1. Save the starter code to a file called hotdog.html
2. Open hotdog.html in your browser
3. Change the answer from "Yes" to "No" by clicking the button
4. Refresh you browser, what happened and why? spoiler.

#### Store the answer in a database

If we want to change the answer and for it to stay changed after we refresh the page, we need to store the answer in our database.

Follow along with this short video tutorial to solve add firebase support to our web app.
<iframe width="560" height="315" src="https://www.youtube.com/embed/2Vf1D-rUMwE" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Final Solution
```
```


### Conclusion
You now have have an appreciation for how websites store your data and you created your very own database and used it to store data about a hotdog.  Science.

<iframe src="https://giphy.com/embed/xT0xeJpnrWC4XWblEk" width="480" height="320" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/whoa-hd-tim-and-eric-xT0xeJpnrWC4XWblEk">via GIPHY</a></p>