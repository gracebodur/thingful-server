Grace Bodur
Ieva Urbaite
Alvin Pierre-Louis

# Link to thingful-client:
# https://github.com/gracebodur/thingful-client.git

# Basic Questions

## 1. What the project does

The project allows you to "rate all the things" 

The main page shows you a list of things with images, descriptions, and ratings and allows you to click each item to open a new thing page.

The individual thing page shows:
• Previous ratings and reviews
• Form to add your own review
• Posting the review does not work

## SERVER

### Two databases:
 1. thingful
 2. thingful-test

#### The databases have three tables:
  1. things
  2. users
  3. reviews

### Endpoints
#### Things endpoints
        • GET /api/things
        • GET /api/things/:thing_id
        • GET /api/things/:thing_id/reviews

#### Reviews endpoints
       • POST /api/reviews
       

### CLIENT 

#### ROUTES:

http://localhost:3000/ - The thing list page

http://localhost:3000/thing/:thingId - The individual thing id page

http://localhost:3000/login - The login page
• No validation for this page
• Not checking the database for user info to validate

http://localhost:3000/register - The registration page
• Doesn't give you confirmation that 
• Validation: does have validation for full name, user name, and password.


QUESTION: Why is GET reviews in the things-router.js?

QUESTION: Why is test for reviews endpoint is listed under Things Endpoints

## 2. How to run the project
• The entry file is ./src/server.js

## 3. Where to find pieces of configuration or important code

• Migrations configuration is in ./postgrator-config.js
• uses PostgreSQL

# Assignment Questions

## 1. How are the syntaxes async and await useful when writing JavaScript code?
• Special syntax to work with promises

• Async before a function means a function always returns a promise. Other values that are non-promises are wrapped in a resolved promise automatically. 

• Await only works inside async funciton and makes Javascript wait until the promise settles and it returns its result. Doesn't cost any CPU resources because the engine can do other jobs in the meantime. It's cleaner syntax than promise.then

## 2. With respect to Knex, how does the transaction method relate to BEGIN and COMMIT syntax in PostgreSQL?
Like BEGIN and COMMIT in PostgreSQL, a transaction in knex allows us to rollback to the previous commit if there is an error in doing something like seeding a database.

More: https://knexjs.org/#Transactions

## 3. What is a "sequence table" in PostgreSQL?
CREATE SEQUENCE creates a new sequence number generator. This involves creating and initializing a new special single-row table with the name name. The generator will be owned by the user issuing the command.

More: https://www.postgresql.org/docs/9.5/sql-createsequence.html

## 4. What does RESTART IDENTITY CASCADE do?
RESTART IDENTIY: 
Automatically restart sequences owned by columns of the truncated table(s).

CASCADE: 
Automatically truncate all tables that have foreign-key references to any of the named tables, or to any tables added to the group due to CASCADE.

More: https://www.postgresql.org/docs/9.2/sql-truncate.html

## 5. What does SELECT setval('blogful_users_id_seq', 1) do?
Reset the sequence object's counter value.

More: https://www.postgresql.org/docs/8.2/functions-sequence.html

# Additional Questions: 


### "What is PostgreSQL SERIAL PRIMARY KEY?"

### What is DISTINCT in PostgreSQL?
DISTINCT eliminates duplicate rows from the results retreived by the SELECT statement. It keeps one row for each group of uplicates. This one row is unpredicatable unless ORDER BY is used to ensure that the desired row appears first. 

### What is db.raw in knex?

### json_strip_nulls
Look at this page: https://www.postgresql.org/docs/9.5/functions-json.html

### json_build_objects

### What is .leftjoin?

### What is Treeize?

### Hints
• If the Postgres user setup for thingful-server gets confusing, you can change the server configurations to use dunder_mifflin user as well as creating the databases using that user.

• Take a look inside the knex service objects, there is a library called treeize. Treeize is a good candidate to read the documentation for in https://npmjs.com. You can try doing a console.log before and after each time treeize is used. Can you find where treeize is being used?

• Take a look at the migrations files, there's a new PostgreSQL syntax for id fields. They're using a type of SERIAL. This would be a good question for a Google search: "What is PostgreSQL SERIAL PRIMARY KEY?"