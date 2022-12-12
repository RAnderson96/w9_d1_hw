# Homework: Full Stack Games Hub App

### Learning Objectives

- Understand the relationship between client, server and database
- Be able to navigate a codebase that you haven't written

## Brief

Your boss has asked to you look over the codebase of a full-stack JavaScript application. The front-end is written in JavaScript using React, the back-end uses an Express server and a MongoDB database. Your task is to make yourself familiar with the codebase.

The application includes a README.md with instructions on running the application.

![Overview of the tech stack and tooling with commands](images/tech_stack_with_commands.png)

*Overview of the tech stack and tooling with commands*

*EDIT: Frontend is now written in React with the command to run `npm start`*

## MVP

### Task

Draw a diagram showing the dataflow through the application starting with a form submission, ending with the re-rendering of the page. This will involve a multi-direction data-flow with the client posting data to the server and the server sending data back to the client with the response. Detail the client, server and database in the diagram and include the names of the files involved in the process.

### Questions

1. What is responsible for defining the routes of the `games` resource?
- The create_router.js file within folders server/helpers. This lays the RESTful route pathing for the ttp request and responses

2. What do you notice about the folder structure?  Whats the client responsible for? Whats the server responsible for?

The folder structure within client follows that of a regular React app. However with the inclusion of the services folder which could be analagous to the Flask frameworks controllers folder. This allows for when a user interacts with the data on client side to invoke an http request to the DB, in this case it either invokes a HTTP action to create a NEW game or DESTROY a game. 

The server folder structures helpers folder is somewhat analagous to the flask frameworks repositories. This allows for the invoked methods on client side to then be 
The server at first is populated on start up by seeds.js. Once this is done the server.js file uses the RESTful route pathways listed in create_router.js to allow for client side data to be added or client requests to be fufilled from the database.




3. What are the the responsibilities of server.js?

The server.js file utilises the express framework. The cors also allows for data requests from public. The create_router.js function is imported and utilised to provide use app the middleware functions at the specified path for the client side.



4. What are the responsibilities of the `gamesRouter`?

This is a specific instance of the createRouter function. This allows for app.use to retrieve the middleware functions of createRouter to provide RESTful routing pathways from our API.



5. What process does the the client (front-end) use to communicate with the server?

HTTP restful routes located within the file GamesService.js located within services folder

6. What optional second argument does the `fetch` method take? And what is it used for in this application? Hint: See [Using Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) on the MDN docs

This takes an js object which contains fetch options which allow for greater control and specicivity of the fetch method. We use the second arugment for the HTTP RESTful routing methods such as POST and DELETE and can also include body and header information for inserting data to the database.


7. Which of the games API routes does the front-end application consume (i.e. make requests to)?

The front-end application only consumes the Get, Post and Delete methods.


8. What are we using the [MongoDB Driver](http://mongodb.github.io/node-mongodb-native/) for?

The MongoDB driver allows for the Mongo client to be able to connect to the database. This is accomplished by using the mongo node argument in Mongo client. When running NPM install it installs the MongoDB driver dependencies.

## Extension

Why do we need to use [`ObjectId`](https://mongodb.github.io/node-mongodb-native/api-bson-generated/objectid.html) from the MongoDB driver?

This allows for access of database items via their unique id which is the ObjectId.


Add to your diagram the dataflow for removing a game.
