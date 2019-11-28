- [Answers of all questions in exam 2 study guide](#answers-of-all-questions-in-exam-2-study-guide)
  - [REST APIs and Fetch API](#rest-apis-and-fetch-api)
  - [JavaScript & JSON](#javascript--json)
  - [Model View Controller, Express API, Middleware and Routing](#model-view-controller-express-api-middleware-and-routing)
  - [Views, Templating, CRUD, MongoDB & ORMs](#views-templating-crud-mongodb--orms)
  - [Sessions, Cookies, Open Authentication](#sessions-cookies-open-authentication)

# Answers of all questions in exam 2 study guide

## REST APIs and Fetch API

1. What is the REST architecture and the 6 constraints?

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

2. What are resources (in REST) and a resource representation? Know how to design a RESTful API and endpoints.

    **a resource** can be any object the API can provide information about. In Instagram’s API, for example, a resource can be a user, a photo, a hashtag. Each resource has a unique identifier. The identifier can be a name or a number.

    **The representation of the state** can be in a JSON format, and probably for most APIs this is indeed the case. It can also be in XML or HTML format.

3. What are the differences between XML and JSON?

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

4. What is Fetch? What do we use it for?

    **The Fetch API** is a simple interface for fetching resources. Fetch makes it easier to make web requests and handle responses than with the older XMLHttpRequest, which often requires additional logic (for example, for handling redirects). Note: Fetch supports the Cross Origin Resource Sharing (CORS).

    A Fetch API provides a fetch() method defined on a window object, which you can use to perform requests and sent it to the server. This method returns a Promise that you can use to retrieve the response of the request

    **we use it for**:

    allowing us to make asynchronous requests, load data outside of the standard page request and loading process, make web pages faster and more responsive, cuts down on the amount of network traffic and loading required on the client and server.

## JavaScript & JSON

1. Understand what a promise is, how to use a promise and chaining.

    **The Promise object** represents the eventual completion (or failure) of an asynchronous operation, and its resulting value.

    A promise is an object that may produce a single value some time in the future: either a resolved value, or a reason that it’s not resolved (e.g., a network error occurred). A promise may be in one of 3 possible states: fulfilled, rejected, or pending. Promise users can attach callbacks to handle the fulfilled value or the reason for rejection.

    **how to use promise and chaining**: Because .then() always returns a new promise, it’s possible to chain promises with precise control over how and where errors are handled. Promises allow you to mimic normal synchronous code’s try/catch behavior.

    the fetch() function returns a promise with the response of the operation.

2. Know JSON syntax and data types.

## Model View Controller, Express API, Middleware and Routing

1. Know the differences between front-end and back end development.
2. What is a technology stack? How do you pick one? Describe/Identify common web technology stacks.
3. Describe the role of each layer of the Model, View, Controller (MVC) architecture.
4. Describe the role/function of the middleware, routing , route & query parameters. Be able to use these.
5. What is Express? What do we use it for?

## Views, Templating, CRUD, MongoDB & ORMs

- Write simple EJS template code.
- Know the different types of NoSQL databases.
- Know the structure of a NoSQL database.
- Identify which CRUD operations map to each SQL or HTTP operation.
- Know the basic methods available in MongoDB to perform CRUD operations.

## Sessions, Cookies, Open Authentication

- Kow what an HTTP session and cookie is. Understand how cookies work.
- What are the different types of cookies? What are some attributes of cookies
(in the HTTP header)?
- What are the different Cookie Laws? How do they apply to us as web
developers?
- How do we manage state on the server-side with cookies?
- What is OAuth? What problems does it solve? How does it benefit the user
and developers?