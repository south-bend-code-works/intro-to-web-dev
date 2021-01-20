<!--

Agenda:
0. House Keeping: Cover any issues / concerns for the course.
1. Review API concepts 
    demonstrate other APIs
        - Cat Fact:
        
          <body>
            <h1>Cat fact: <span id="cat-fact"></span></h1>
          </body>

          <script>

            var catFactEle = document.getElementById("cat-fact")

            var hitApi = (url) => {
              fetch(url)
                .then(res => res.json())
                .then((data) => {
                  catFactEle.innerHTML = data.text
                })
            }

            hitApi("https://cat-fact.herokuapp.com/facts/random?animal_type=cat")

          </script>

        - Random Fox Image:

          <body>
            <h1>Random Fox:</h1>
            <img id="fox" src=""/>
          </body>

          <script>

            var foxEle = document.getElementById("fox")

            var hitApi = (url) => {
              fetch(url)
                .then((res) => res.json())
                .then((data) => {
                  var imageSrc = data.image
                  foxEle.src = imageSrc
                })
            }

            hitApi("https://randomfox.ca/floof/")

          </script>

        

2. 
3. Walk through adding Giphy random gif to Advanced Chat
5. (last 5 minutes)
    - Review Weekly Project & what students can do to prep now.

-->