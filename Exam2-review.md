- [Answers of all questions in exam 2 study guide](#answers-of-all-questions-in-exam-2-study-guide)
  - [REST APIs and Fetch API](#rest-apis-and-fetch-api)
    - [1. What is the REST architecture and the 6 constraints?](#1-what-is-the-rest-architecture-and-the-6-constraints)
    - [2. What are resources (in REST) and a resource representation? Know how to design a RESTful API and endpoints.](#2-what-are-resources-in-rest-and-a-resource-representation-know-how-to-design-a-restful-api-and-endpoints)
    - [3. What are the differences between XML and JSON?](#3-what-are-the-differences-between-xml-and-json)
    - [4. What is Fetch? What do we use it for?](#4-what-is-fetch-what-do-we-use-it-for)
  - [JavaScript & JSON](#javascript--json)
    - [1. Understand what a promise is, how to use a promise and chaining.](#1-understand-what-a-promise-is-how-to-use-a-promise-and-chaining)
    - [2. Know JSON syntax and data types.](#2-know-json-syntax-and-data-types)
  - [Model View Controller, Express API, Middleware and Routing](#model-view-controller-express-api-middleware-and-routing)
    - [1. Know the differences between front-end and back end development.](#1-know-the-differences-between-front-end-and-back-end-development)
    - [2. What is a technology stack? How do you pick one? Describe/Identify common web technology stacks.](#2-what-is-a-technology-stack-how-do-you-pick-one-describeidentify-common-web-technology-stacks)
    - [3. Describe the role of each layer of the Model, View, Controller (MVC) architecture.](#3-describe-the-role-of-each-layer-of-the-model-view-controller-mvc-architecture)
    - [4. Describe the role/function of the middleware, routing, route & query parameters, views. Be able to use these.](#4-describe-the-rolefunction-of-the-middleware-routing-route--query-parameters-views-be-able-to-use-these)
    - [5. What is Express? What do we use it for?](#5-what-is-express-what-do-we-use-it-for)
  - [Views, Templating, CRUD, MongoDB & ORMs](#views-templating-crud-mongodb--orms)
    - [1. Write simple EJS template code.](#1-write-simple-ejs-template-code)
    - [2. Know the different types of NoSQL databases.](#2-know-the-different-types-of-nosql-databases)
    - [3. Know the structure of a NoSQL database.](#3-know-the-structure-of-a-nosql-database)
    - [4. Identify which CRUD (Create, Read, Update, Delete) operations map to each SQL or HTTP operation.](#4-identify-which-crud-create-read-update-delete-operations-map-to-each-sql-or-http-operation)
    - [5. Know the basic methods available in MongoDB to perform CRUD operations.](#5-know-the-basic-methods-available-in-mongodb-to-perform-crud-operations)
  - [Sessions, Cookies, Open Authentication](#sessions-cookies-open-authentication)
    - [1. Know what an HTTP session and cookie is. Understand how cookies work.](#1-know-what-an-http-session-and-cookie-is-understand-how-cookies-work)
    - [2. What are the different types of cookies? What are some attributes of cookies (in the HTTP header)?](#2-what-are-the-different-types-of-cookies-what-are-some-attributes-of-cookies-in-the-http-header)
    - [3. What are the different Cookie Laws? How do they apply to us as web developers?](#3-what-are-the-different-cookie-laws-how-do-they-apply-to-us-as-web-developers)
    - [4. *How do we manage state on the server-side with cookies?](#4-how-do-we-manage-state-on-the-server-side-with-cookies)
    - [5. *What is OAuth? What problems does it solve? How does it benefit the user and developers?](#5-what-is-oauth-what-problems-does-it-solve-how-does-it-benefit-the-user-and-developers)

# Answers of all questions in exam 2 study guide

## REST APIs and Fetch API

### 1. What is the REST architecture and the 6 constraints?

**REST** is a software architectural style(not a technology) that defines a set of constraints to be used for creating Web services. It is a way of designing API for the web, it is not a formal standard, but rather an approach to designing APIs, this means there are varying levels of restfulness.

**REpresentational State Transfer**: It means when a RESTful API is called, the server will transfer to the client a representation of the state of the requested resource.

**constrains:**

- uniform interface

    all resources should be accessible through a common approach such as HTTP GET and similarly modified using a consistent approach.

    The request to the server has to include a resource identifier

    The response the server returns include enough information so the client can modify the resource

    Each request to the API contains all the information the server needs to perform the request, and each response the server returns contain all the information the client needs in order to understand the response.

    Hypermedia as the engine of application state — this may sound a bit cryptic, so let’s break it down: by application we mean the web application that the server is running. By hypermedia we refer to the hyperlinks, or simply links, that the server can include in the response. The whole sentence means that the server can inform the client , in a response, of the ways to change the state of the web application. If the client asked for a specific user, the server can provide not only the state of that user but also information about how to change the state of the user, for example how to update the user’s name or how to delete the user. It is easy to think about the way it’s done by thinking about a server returning a response in HTML format to a browser (which is the client). The HTML will include tags with links (this is the hypermedia part) to another web page where the user can be updated (for example a link to a ‘profile settings’ page). To put all of this in perspective, most web pages do implement hypermedia as the engine of application state, but the most common web APIs do not adhere to this constraint. To further understand this concept, I highly recommend watching this 30 minutes YouTube video.

- stateless

    server will not store anything about latest HTTP request client made. It will treat each and every request as new. No session, no history. State is maintained by the client.

    Stateless means the server does not remember anything about the user who uses the API. It doesn’t remember if the user of the API already sent a GET request for the same resource in the past, it doesn’t remember which resources the user of the API requested before, and so on.

    Each individual request contains all the information the server needs to perform the request and return a response, regardless of other requests made by the same API user.

- cacheable

    to enable large scale services, caching shall be applied to resources when application and then there resources MUST declare themselves cacheable.

    This means that the data the server sends contain information about whether or not the data is cacheable. If the data is cacheable, it might contain some sort of a version number. The version number is what makes caching possible: since the client knows which version of the data it already has (from a previous response), the client can avoid requesting the same data again and again. The client should also know if the current version of the data is expired, in which case the client will know it should send another request to the server to get the most updated data about the state of a resource.

- client-server

    a client application and a server application MUST be able to evolve separately without and any dependency on each other. A client should know only resource URIs and that's all.

    The client and the server act independently, each on its own, and the interaction between them is only in the form of requests, initiated by the client only, and responses, which the server send to the client only as a reaction to a request. The server just sits there waiting for requests from the client to come. The server doesn’t start sending away information about the state of some resources on its own.

- layered system

    a RESTful architecture can be composed of several hierarchical layers that the client does not to be aware of. There layers (e.g. security, caching, load-balancing) should not affect the request or the response.

    Between the client who requests a representation of a resource’s state, and the server who sends the response back, there might be a number of servers in the middle. These servers might provide a security layer, a caching layer, a load-balancing layer, or other functionality. Those layers should not affect the request or the response. The client is agnostic as to how many layers, if any, there are between the client and the actual server responding to the request.

- code on demand(optional)

    REST allows client functionality to be extend by downloading and executing code in the form of applets or scripts. The simplifies clients by reducing the number of features required to be pre-implemented.

    This constraint is optional — an API can be RESTful even without providing code on demand.

    The client can request code from the server, and then the response from the server will contain some code, usually in the form of a script, when the response is in HTML format. The client then can execute that code.

### 2. What are resources (in REST) and a resource representation? Know how to design a RESTful API and endpoints.

**a resource** can be any object the API can provide information about. In Instagram’s API, for example, a resource can be a user, a photo, a hashtag. Each resource has a unique identifier. The identifier can be a name or a number.

**The representation of the state** can be in a JSON format, and probably for most APIs this is indeed the case. It can also be in XML or HTML format.

### 3. What are the differences between XML and JSON?

JSON is unlike XML:

- JSON is shorter
- JSON is quicker to read and write
- JSON can use arrays
- XML has to be parsed with an XML parser. JSON can be parsed by a standard JavaScript function.

JSON is like XML:

- Both JSON and XML are "self describing" (human readable)
- Both JSON and XML are hierarchical (values within values)
- Both JSON and XML can be parsed and used by lots of programming languages
- Both JSON and XML can be fetched with AJAX

Why JSON is better than XML:

XML is hard to parse, JSON is parsed into a ready-to-use JavaScript object.

### 4. What is Fetch? What do we use it for?

**The Fetch API** is a simple interface for fetching resources. Fetch makes it easier to make web requests and handle responses than with the older XMLHttpRequest, which often requires additional logic (for example, for handling redirects). Note: Fetch supports the Cross Origin Resource Sharing (CORS).

A Fetch API provides a fetch() method defined on a window object, which you can use to perform requests and sent it to the server. This method returns a Promise that you can use to retrieve the response of the request

**we use it for**:

allowing us to make asynchronous requests, load data outside of the standard page request and loading process, make web pages faster and more responsive, cuts down on the amount of network traffic and loading required on the client and server.

## JavaScript & JSON

### 1. Understand what a promise is, how to use a promise and chaining.

**The Promise object** represents the eventual completion (or failure) of an asynchronous operation, and its resulting value.

A promise is an object that may produce a single value some time in the future: either a resolved value, or a reason that it’s not resolved (e.g., a network error occurred). A promise may be in one of 3 possible states: fulfilled, rejected, or pending. Promise users can attach callbacks to handle the fulfilled value or the reason for rejection.

**how to use promise and chaining**: Because .then()(fulfilled) .catch()(rejected) always returns a new promise, it’s possible to chain promises with precise control over how and where errors are handled. Promises allow you to mimic normal synchronous code’s try/catch behavior.

### 2. Know JSON syntax and data types.

Types:

- String
- Number
- Object
- Array
- Boolean
- Null

## Model View Controller, Express API, Middleware and Routing

### 1. Know the differences between front-end and back end development.

**Frontend refers to the client-side, whereas backend refers to the server-side of the application**. Both are crucial to web development, but their roles, responsibilities and the environments they work in are totally different. Frontend is basically what users see whereas backend is responsible for saving, managing, and sometimes processing data(i.e. how it works)

why server-side:

- efficient storage and delivery of information
- customize user experience
- access control
- data collection and analysis
- heavy computation

### 2. What is a technology stack? How do you pick one? Describe/Identify common web technology stacks.

**When referring to the technology or solution stack** - this includes the tools, frameworks and technologies used to develop a web application.

front-end or client-side:

- HTML
- CSS
- JavaScript
- Frameworks: Bootstrap, Foundation, Angular, React, Vue

back-end or server-side:

- Operation System
- Web server
- Database
- Programming Language
- Web Development Frameworks

**How do you pick one**:

There is no straightforward, right answer:

- user before developers, considering the needs of users first.
- what problem need to be solved, the technology you choose should depend on the problem want to solve,
- what is the experience of the people developing the solution, what is your timeline? learning curve? resources available?
- what are the technical requirement? performance, scalability and security
- what is the cost? licensing, hosting
- check out the ecosystem. documentations and communities

**common web technology stacks**:

- MEAN: MongoDB, Express, Angular, NodeJS
- MERN: MongoDB, Express, React, NodeJS

### 3. Describe the role of each layer of the Model, View, Controller (MVC) architecture.

**The model**: central component and represents the data structure independent from the interface. Where the data is stored.

**The view**: create representations of information, the interface of the application. How the data is displayed to the users.

**The controller**: manages the connections between the view and the model. The application logic.

### 4. Describe the role/function of the middleware, routing, route & query parameters, views. Be able to use these.

**Middleware**: In contrast to vanilla Node, where your request flow through only one function, Express has a middleware stack, which is effectively an array of functions. It can execute any codes; make changes to the requests and response objects; end the request-response cycle and send the response back to the client; call the next function in the middleware stack.

**Routing**: Routing is a lot like middleware, but the functions are called only when you visit a specific URL with a specific HTTP method. For example, you could only run a request handler when the browser visits. Routing refers to how an application's endpoint (URLs) respond to client requests.

**Route & Query parameters**:

- Route parameters are named URL segments that are used to capture the values specified at their position in the URL.
- Query parameters are used to specify optional filters, it is not a part of the route path, should begin with '?' and key-value query, combine multiple queries use '&'

**Views**: Views are used to dynamically generate HTML on the server and send it back to the client.

### 5. What is Express? What do we use it for?

**Express** is a minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications, to help organize your web application into an MVC architecture on the server side.

**What do we use it for**: It is designed for building web applications and APIs. It has been called the de facto standard server framework for Node.js

## Views, Templating, CRUD, MongoDB & ORMs

### 1. Write simple EJS template code.

- <%  - 'Scriptlet' tag, for control-flow, no output
- <%_ - 'Whitespace Slurping' Scriptlet tag, strips all whitespace before it
- <%= - Outputs the value into the template (escaped)
- <%- - Outputs the unescaped value into the template
- <%# - Comment tag, no execution, no output
- <%% - Outputs a literal '<%'
- %%> - Outputs a literal '%>'
- %>  - Plain ending tag
- -%> - Trim-mode ('newline slurp') tag, trims following newline
- _%> - 'Whitespace Slurping' ending tag, removes all whitespace after it

```HTML
Hi <%= name %>!
You were born in <%= birthyear %>, so that means you're
    <%= (new Date()).getFullYear() - birthyear %> years old.
<% if (career) { -%>
    <%=: career | capitalize %> is a cool career!
<% } else { -%>
    Haven't started a career yet? That's cool.
<% } -%>
Oh, let's read your bio: <%- bio %> See you later!
```

### 2. Know the different types of NoSQL databases.

- key-value: Riak, Amazon S3(Dynamo)
- graph: Neo4J
- column: HBase, Cassandra
- document: MongoDB

### 3. Know the structure of a NoSQL database.

Use document-based database as example:

- Collections: collections in Mongo are equivalent to tables in relational databases. They can hold multiple JSON documents.
- Documents: documents are equivalent to records or rows of data in SQL. While a SQL row can reference data in other tables, Mongo documents usually combine that in a document.
- Fields: fields or attributes are similar to columns in a SQL table.
- Schema: while mongo is schema-less, SQL defines a schema via the table definition. A Mongoose schema is a document data structure(or shape of the document) that is enforced via the application layer.
- Models: models are higher-order constructors that take a schema and create an instance of a document equivalent to records in a relational database.

### 4. Identify which CRUD (Create, Read, Update, Delete) operations map to each SQL or HTTP operation.

| Operation       | SQL    | HTTP           | RESTful WS |
|-----------------|--------|----------------|------------|
| Create          | INSERT | PUT/POST       | POST       |
| Read(Retrieve)  | SELECT | GET            | GET        |
| Update(Modify)  | UPDATE | PUT/POST/PATCH | PUT        |
| Delete(Destroy) | DELETE | DELETE         | DELETE     |

### 5. Know the basic methods available in MongoDB to perform CRUD operations.

- mongoDB connection:

```js
const mongodb = ("mongodb+srv://" + USERNAME + ":" + PASSWORD + "@" + HOST + "/" + DATABASE)
mongoose.connect(mongodb, (useNewUrlParser: true, retryWrites: true))
```

- define data models

```js
const mongoose = require("mongoose");
const Schema = mongoose.Schema;
const BookSchema = new Schema({
    title: {
        type: String,
        required: function(){
            return this.title.length > 3:
        }
    },
    author: {
        type: String
    }
})

model.exports = mongoose.model('book', BookSchema)
```

- CREATE:

```js
router.post('/', function(req, res){
    let book = new Book(req.body);
    book.save();
    res.status(201).send(book);
})
```

- READ:

```js
router.get("/", function(req, res) {
    Book.find({}, functino(err, book_list){
        res.json(book_list)
    });
})
// RETRIEVE a specific book
router.get('/:bookId', function(req, res) {
    Book.findById(req.params.bookId, function(err, book){
        res.json(book)
    });
})
```

- UPDATE:

```js
router.put("/:bookId", function(req, res){
    Book.findById(req.params.bookId, function(err, book){
        book.title = req.body.title;
        book.author = req.body.author;
        book.save();
        res.json(book);
    });
})
```

- DELETE:

```js
router.delete("/bookId", function(req, res){
    Book.findById(req.params.bookId, function(err, book){
        book.remove(function(err){
            if (err) {
                res.status(500).send(err);
            }else{
                res.status(204).send('removed');
            }
        });
    });
})
```


## Sessions, Cookies, Open Authentication

### 1. Know what an HTTP session and cookie is. Understand how cookies work.

**HTTP sessions** is an industry standard feature that allows Web servers to maintain user identity and to store user-specific data during multiple request/response interactions between a client application and a Web application. Session can store variables - such as access rights and localization settings.

**An HTTP cookie** is a small piece of data sent from a website/server to a browser and stored on the user's computer by the user's web browser while the user is browsing. Cookies were designed to be a reliable mechanism for websites to remember stateful information or to record the user's browsing activity. Cookie can be attached to every HTTP request using the cookie HTTP Header. Mainly used for (1) Session management, (2) personalization, (3) tracking.

**How cookies work**

![](https://i1.wp.com/4.bp.blogspot.com/-FnbFMxnKkV4/WV565AN7ifI/AAAAAAAAQZg/5_p-m1oxBqUx2CCqyqS3Y9JAUwmGO34nQCLcBGAs/s1600/1.png?zoom=2&w=687&ssl=1)

### 2. What are the different types of cookies? What are some attributes of cookies (in the HTTP header)?

**Different types of cookies**

- Session Cookie

    This type of cookies dies when the browser is closed because they are stored in the browser's memory. Can be used for shopping carts or anonymous user preferences that don't need to be saved across a multiple browser sessions.

- Persistent or Permanent Cookie

    Stored in a file or database in the browser. Expire at a specific data or after a specific length of time.

- Third Party Cookie

    A cookie set by a different domain from the server. These cookies are used for tracking patterns and advertising.

- Secure Cookie

    Cookies that are only transmitted over an encrypted connection. Browser won't send the cookie over an insecure connection.

- Zombie or Evercookies or Supercookies

    Cookies that get recreated after they are deleted and persist on the client all the time. Popular with advertising and analytics trackers. VERY HARD TO DELETE.

**Some attributes of cookies in the HTTP header**

- Name: Specifies the name of a cookie for retrieving the cookie
- Value: Specifies the value of cookie. Max size of all cookies is 4093 bytes per domain
- Secure: Specifies if the cookie should only be transmitted over encrypted HTTPS connections. Default is false
- Domain: Specifies the domain name associated with the cookie. Helps the browser determine when to send a cookie with HTTP requests (don't want to send all cookies to all servers)
- Path: Specifies a server path ("/", "/users/", "/login") for sending the cookie.
- HTTPOnly: Means the cookie will only be available on the HTTP protocol, not accessible to JavaScript
- Expires: Specify when the cookie expires and should no longer be sent with HTTP Requests. If set to 0 the cookie will expire when the browser closes

```html
Set-Cookie: <cookie-name>=<cookie-value> 
Set-Cookie: <cookie-name>=<cookie-value>; Expires=<date>
Set-Cookie: <cookie-name>=<cookie-value>; Max-Age=<non-zero-digit>
Set-Cookie: <cookie-name>=<cookie-value>; Domain=<domain-value>
Set-Cookie: <cookie-name>=<cookie-value>; Path=<path-value>
Set-Cookie: <cookie-name>=<cookie-value>; Secure
Set-Cookie: <cookie-name>=<cookie-value>; HttpOnly
 <!-- Multiple directives are also possible, for example: -->
Set-Cookie: <cookie-name>=<cookie-value>; Domain=<domain-value>; Secure; HttpOnly
```

### 3. What are the different Cookie Laws? How do they apply to us as web developers?

 The EU Directive 2009/136/EC of the European Parliament means that before somebody can store or retrieve any information from a computer, mobile phone or other device, the user must give informed consent to do so.

 Make developers to follow the law when they're collecting personal data from individuals, the users must five informed consent to do so.

### 4. *How do we manage state on the server-side with cookies?

Problems with Server Side State:
- Sessions based on Session ID cookies are not stable and hard to scale
- Cookies are not supported by some mobile and desktop applications
- Cookies only work for a single domain
- to address there issues there are new approaches to managing session state by saving state on the client like JSON Web Tokens

Use Passport.JS:

Passport.JS is an authentication middleware for Node, it is designed to authenticate requests. It takes away a lot of the headaches of authenticating users and maintaining their state across request.

### 5. *What is OAuth? What problems does it solve? How does it benefit the user and developers?

**OAuth** or Open Authentication is an open-standard authorization protocol or framework used for authorization. This is also known as a secure, third-party, delegated authorization.

**For users**:

- It allows a user to log into a website like AirBnB via some other service, like Gmail
- Don't have to memorize multiple passwords

**For developers**:

- It lets you authenticate a user without having to implement log in