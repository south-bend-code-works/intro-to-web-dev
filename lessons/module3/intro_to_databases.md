---
layout: default
---

# Intro to Databases

## Goal
By the end of this lesson, you will have:

1. A basic understanding of why we use databases.
2. A brief overview of the two of the most popular types of databases.
    1. Relational Databases
    2. Document Store Databases

## Why do we use databases?

<p>So far, all of the data and content we displayed in our webpages has been hard-coded into our HTML documents.  While this may work for simple websites, it won't work for more sophisticated web applications, such as online stores.</p>

<p>The web uses the HTTP protocol, which is a "stateless protocol".  This is fancy speak for "If you refresh your web-browser any changes you made to your HTML will be lost".  In the early days of the web, this was not too bad as we were mostly using the web to share research papers and pictures of our cats.  As time passed, the complexity of our web applications increased, and we began to need to save the "state" of the site so we could recall it again later; this didn't play nice with our stateless http protocol.  For example, an online store needs to save the items we've added to our cart so we can purchase them later.</p>

<p>Therefore, in order to save "state", developers needed to devise other ways to store data.  For example, you may have heard of <b>cookies</b>, which are tiny text files saved by your web browser that are used to store the "state of things".  When a website loads, it can check if a cookie exists, and if so, read any data that was stored in it.  Thus, we could save a list of all the items in our shopping cart into a cookie for later.  Unfortunately, cookies have a major drawback in that they are not very useful if you are using more than one device or browser.  Additionally, they can be blocked or cleared by the user so they are not a reliable way to store and retrieve information.</p>

<p>In order to reliable store and retrieve data, developers turned to <b>databases</b>, which run on separate servers.  Websites can query, or request data from, those databases.  For example, we can store the users shopping cart to our centralized database and no mater which device or browser we use, we can easily query our database to find all of the items in our cart.  Neato!</p>

## Types of Databases
<p>The objective for any database is simple; store data about objects.</p>

<p>For example, if you wanted to store information about people and their favorite books you might want to save each users name, age, and gender, as well as any books they have read.</p>

Let's compare and contrast how we might structure this data in two of the most popular styles of databases: 
1. Relational Databases (aka a SQL Database)
2. Document Store Databases (aka a noSQL Database)

### Relational Database
When you think of relational databases, it'a easiest to conceptually think of storing data in a series of related spreadsheets.  In our example, we might have one table of data called <b>users</b> and another called <b>books</b>.  These tables can be related, or _joined_, together by a common key, in this case, the username.

##### Users Table

| username | age | gender |
| ------------- | ------------- | ------------- |
| Chris | 42 | M |
| Maisie | 2 | F |
| Sisaye | 12 | F |

##### Books Table

| username        | book_title|
| ------------- | -----|
| Chris     | Game of Thrones |
| Chris     | Ready Player One |
| Maisie      | If you give a mouse a cookie |
| Maisie      | Skippyjon Jones |
| Sisaye |    The Twilight Saga |

##### Query and Results
We can query data from these tables using SQL, or structured query language.  The SQL query to get all of the data from both tables would look like:
```
select username, age, gender, book_title from users 
    inner join books on users.username = books.username;
```

The result of this query would be a new table of data that looks like:

| username        | age| gender| book_title|
| ------------- | ----- |
| Chris     | 42 | M | Game of Thrones |
| Chris     | 42 | M | Ready Player One |
| Maisie     | 2 | F |If you give a mouse a cookie |
| Maisie       | 2 | F | Skippyjon Jones |
| Sisaye | 12 | F|   The Twilight Saga |

And that's just about it.

### Document Store Databases
Instead of storing data in tables, a Document Store Database seeks to keep all of the related data about each user and the books that user has read in a single <b>document</b>.  Groups of these documents are then organized into <b>collections</b>.


Simply put, collections contain sets documents.  Each document contains any number of attributes and values (key / value pairs) that describe that document's data.

The easiest way to think about how to structure data in a Document Store is to conceptualize how we would store the data in JavaScript Objects.  Typically, Document Stores are built using some flavor of JSON, which stands for JavaScript Object Notation.  This fact makes it particularly easy to use Document Store Databases with JavaScript in your websites.

In our example, we would have <b>1 collection</b> with <b>3 documents</b> (one document per user).  In JSON, it might look something like this:
```
{
   "favorite_books":{
      "0":{
         "username":"chris",
         "age":42,
         "gender":"M",
         "books":[
            "Game of Thrones",
            "Ready Player One"
         ]
      },
      "1":{
         "username":"maisie",
         "age":2,
         "gender":"F",
         "books":[
            "Skippyjon Jones",
            "If you bring a mouse a cookie"
         ]
      },
      "2":{
         "username":"sisaye",
         "age":12,
         "gender":"F",
         "books":[
            "The Twilight Saga"
         ]
      }
   }
}
```

## Conclusion

<p>Databases can save our data, very nice!</p>

Developers can choose between Relational and Document Store Databases when saving data for their websites.  Next, you will create your very own instance of Google's Firestore Database (hint, it's a a Document Database).

<iframe src="https://giphy.com/embed/xT0BKpLyoxVtvjtVks" width="480" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/pbs-data-its-okay-to-be-smart-big-xT0BKpLyoxVtvjtVks">via GIPHY</a></p>