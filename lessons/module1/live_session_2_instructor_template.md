<!--

 _____  ___    ___    _  _     _____  ___   _____     ___    ___    _   _  ___    ___    _____  _____  _____  ___   
(  _  )(  _`\ (  _`\ (_)(_)   (  _  )|  _`\(_   _)   (  _`\ (  _`\ ( ) ( )(  _`\ |  _`\ (  _  )(_   _)(  _  )|  _`\ 
| (_) || (_(_)| ( (_)| || |   | (_) || (_) ) | |     | ( (_)| (_(_)| `\| || (_(_)| (_) )| (_) |  | |  | ( ) || (_) )
|  _  |`\__ \ | |  _ | || |   |  _  || ,  /  | |     | |___ |  _)_ | , ` ||  _)_ | ,  / |  _  |  | |  | | | || ,  / 
| | | |( )_) || (_( )| || |   | | | || |\ \  | |     | (_, )| (_( )| |`\ || (_( )| |\ \ | | | |  | |  | (_) || |\ \ 
(_) (_)`\____)(____/'(_)(_)   (_) (_)(_) (_) (_)     (____/'(____/'(_) (_)(____/'(_) (_)(_) (_)  (_)  (_____)(_) (_)
                                                                                                                    
                                                                                                                    
http://patorjk.com/software/taag/#p=display&f=Puffy&t='Fin

Agenda:

0. House Keeping: Cover any issues / concerns for the course.
    
1. Using functions and basic logic in JavaScript
2. Learn the Document Object Model (DOM) and combine HTML, CSS, and JavaScript to build interactive websites. 
3. Hosting your website on Github
4. (last 5 minutes)
    - Review Final Project Part 2 
    - Talk about the upcoming lab and it's format
-->


<!--
 _  _   _  _____  ___    ___    ___    _____  _____  _  _   _  ___       _____  _____  _   _  _____  ___    ___    ___    _  ___   _____ 
(_)( ) ( )(_   _)(  _`\ (  _`\ |  _`\ (  _  )(_   _)(_)( ) ( )(  _`\    (___  )(  _  )( ) ( )(  _  )(  _`\ (  _`\ |  _`\ (_)(  _`\(_   _)
| || `\| |  | |  | (_(_)| ( (_)| (_) )| (_) |  | |  | || `\| || ( (_)       | || (_) || | | || (_) || (_(_)| ( (_)| (_) )| || |_) ) | |  
| || , ` |  | |  |  _)_ | |___ | ,  / |  _  |  | |  | || , ` || |___     _  | ||  _  || | | ||  _  |`\__ \ | |  _ | ,  / | || ,__/' | |  
| || |`\ |  | |  | (_( )| (_, )| |\ \ | | | |  | |  | || |`\ || (_, )   ( )_| || | | || \_/ || | | |( )_) || (_( )| |\ \ | || |     | |  
(_)(_) (_)  (_)  (____/'(____/'(_) (_)(_) (_)  (_)  (_)(_) (_)(____/'   `\___/'(_) (_)`\___/'(_) (_)`\____)(____/'(_) (_)(_)(_)     (_)  
                                                                                                                                         
                                                                                                                                         
Goals:
- Get them to use JavaScript on some site they have locally
- show an alert to explain that JS is the "interactive" part
- interact with DOM by editing some element
- show an onClick event that triggers an alert via a <button>
-->

<!-- Step 1: An Alert -->
<!DOCTYPE html>
<html>
    <body>
        <p>Hello, World!</p>
        <script>
            alert("AHHHHHHHHHHHHH");
        </script>
    </body>
</html>

<!-- Step 2: An Alert via a button click -->
<!DOCTYPE html>
<html>
    <body>
        <button onclick="sayHello()">Hello, World!</button>
        <script>
            function sayHello() {
                alert("POOOOOOOOOOOOOP")
            }
        </script>
    </body>
</html>

<!-- Step 3: Use DOM events -->
<!DOCTYPE html>
<html>
    <body>
        <button id="btn">Hello, World!</button>
        <script>
            var btn = document.getElementById("btn")

            function sayHello() {
                alert("POOOOOOOOOOOOOP")
            }

            btn.onclick = sayHello
        </script>
    </body>
</html>

<!-- Step 4: Edit the DOM -->
<!DOCTYPE html>
<html>
    <body>
        <button id="btn">Hello, World!</button>
        <script>
            var btn = document.getElementById("btn")

            function sayHello() {
                btn.innerText = "FAAAAAAARRRRRTTTTTS"
            }

            btn.onclick = sayHello
        </script>
    </body>
</html>
