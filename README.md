# Angular and Node Example App

# Getting started

- Install MongoDB Community Edition ([instructions](https://docs.mongodb.com/manual/installation/#tutorials)) and run it by executing `mongod`
- Make sure you have the [Angular CLI](https://github.com/angular/angular-cli#installation) installed globally. I've used [Yarn](https://yarnpkg.com) to manage the dependencies, so I strongly recommend you to use it. you can install it from [Here](https://yarnpkg.com/en/docs/install).

## Steps to install App

- If angular cli, Nodejs and mongodb is working correct then move to second step are else follow the Getting started procedure
- Clone the repository using command git clone https://github.com/AJAYMORE06/blogging-website.git 
 or download.
- run cd blogging-website
- run npm install

- run npm start 


![Image of adduser](https://raw.githubusercontent.com/ajaymore06/blogging-website/master/screens/npmfinish.JPG)


- once completed open any browser type url http://localhost:4200

### for more screenshots move to end 

### Building the project
Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `-prod` flag for a production build.


## FrontEnd Functionality overview

**General functionality:**

- Authenticate users via JWT (login/signup pages + logout button on settings page)
- CRUD users (sign up & settings page - no deleting required)
- CRUD Articles
- CRUD Comments on articles (no updating required)
- GET and display paginated lists of articles
- Favorite articles
- Follow other users

**The general page breakdown looks like this:**

- Home page (URL: /#/ )
    - List of tags
    - List of articles pulled from either Feed, Global, or by Tag
    - Pagination for list of articles
- Sign in/Sign up pages (URL: /#/login, /#/register )
    - Uses JWT (store the token in localStorage)
    - Authentication can be easily switched to session/cookie based
- Settings page (URL: /#/settings )
- Editor page to create/edit articles (URL: /#/editor, /#/editor/article-slug-here )
- Article page (URL: /#/article/article-slug-here )
    - Delete article button (only shown to article's author)
    - Render markdown from server client side
    - Comments section at bottom of page
    - Delete comment button (only shown to comment's author)
- Profile page (URL: /#/profile/:username, /#/profile/:username/favorites )
    - Show basic user info
    - List of articles populated from author's created articles or author's favorited articles

# Backend code Overview

## Dependencies

- [expressjs](https://github.com/expressjs/express) - The server for handling and routing HTTP requests
- [express-jwt](https://github.com/auth0/express-jwt) - Middleware for validating JWTs for authentication
- [jsonwebtoken](https://github.com/auth0/node-jsonwebtoken) - For generating JWTs used by authentication
- [mongoose](https://github.com/Automattic/mongoose) - For modeling and mapping MongoDB data to javascript 
- [mongoose-unique-validator](https://github.com/blakehaswell/mongoose-unique-validator) - For handling unique validation errors in Mongoose. Mongoose only handles validation at the document level, so a unique index across a collection will throw an exception at the driver level. The `mongoose-unique-validator` plugin helps us by formatting the error like a normal mongoose `ValidationError`.
- [passport](https://github.com/jaredhanson/passport) - For handling user authentication
- [slug](https://github.com/dodo/node-slug) - For encoding titles into a URL-friendly format

## Application Structure

- `server.js` - The entry point to our application. This file defines our express server and connects it to MongoDB using mongoose. It also requires the routes and models we'll be using in the application.
- `server/config/` - This folder contains configuration for passport as well as a central location for configuration/environment variables.
- `server/routes/` - This folder contains the route definitions for our API.
- `server/models/` - This folder contains the schema definitions for our Mongoose models.

## Error Handling

In `server/routes/api/index.js`, we define a error-handling middleware for handling Mongoose's `ValidationError`. This middleware will respond with a 422 status code and format the response to have [error messages the clients can understand]()

## Authentication

Requests are authenticated using the `Authorization` header with a valid JWT. We define two express middlewares in `routes/auth.js` that can be used to authenticate requests. The `required` middleware configures the `express-jwt` middleware using our application's secret and will return a 401 status code if the request cannot be authenticated. The payload of the JWT can then be accessed from `req.payload` in the endpoint. The `optional` middleware configures the `express-jwt` in the same way as `required`, but will *not* return a 401 status code if the request cannot be authenticated.

# screens

![Image of adduser](https://raw.githubusercontent.com/ajaymore06/blogging-website/master/screens/homepage.png)

![Image of adduser](https://raw.githubusercontent.com/ajaymore06/blogging-website/master/screens/details.png)

![Image of adduser](https://raw.githubusercontent.com/ajaymore06/blogging-website/master/screens/editprofile.png)

![Image of adduser](https://raw.githubusercontent.com/ajaymore06/blogging-website/master/screens/addarticle.png)

![Image of adduser](https://raw.githubusercontent.com/ajaymore06/blogging-website/master/screens/myprofile.png)

![Image of adduser](https://raw.githubusercontent.com/ajaymore06/blogging-website/master/screens/topheader.png)

![Image of adduser](https://raw.githubusercontent.com/ajaymore06/blogging-website/master/screens/Screenshot%20(62).png)

![Image of adduser](https://raw.githubusercontent.com/ajaymore06/blogging-website/master/screens/Screenshot%20(63).png)


