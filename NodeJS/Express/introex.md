# Express
- Express is the tool built on top of Node.js that makes your life easy. It provides a clean, simple set of tools (like `app.get()`, `app.post()`, and `express.json()`) so you can build backend servers quickly without reinventing the wheel.
- Install : `npm install express`.

# Routes
- Routes essentially just match a request’s HTTP verb (e.g. GET or POST) and URL path to the appropriate set of middleware functions - the controllers.
- eg: `app.get("/message", (req, res) => res.send("Hello, world!"));`
- In above code, `app.get("/message"...` tells us that this route will match any GET requests that go through the `app` router (which is our whole server!) to the `/message` path.

## Paths
- The first argument we pass a route is the path to match, which can either be a string or a regular expression. `/messages` matches that exactly, while `/messages/all` only matches if the path is `/messages/all` (not `/messages`, nor `/messages/new`).
- With string paths, we can also use `{}` to make characters optional. 
- With `*` (a “splat” or “wildcard”), we can match any number of any characters.
- A common use case for a splat would be as a catch-all for all otherwise unmatched paths, e.g. for custom 404 error handling.
-  
```
// Matches / and /odin as well as /sdds8fjsdifhj98sdfh
"/{*splat}"

```
- NOTE: Orders matters

## Route Parameters
- Route parameters are named URL segments used to capture dynamic values at specific positions in the URL. The captured values are automatically populated in the `req.params` object
- What if we wanted to have a route for all messages for any username, for example, `/odin/messages` or `/thor/messages`? Just like with React Router, we can use route parameters, and a path can contain as many of these parameters as we need.
- To denote such paramters we can use `:` followed by name of characters
- Eg:
-   
```
app.get('/:username/message',(req,res)=>{
    console.log(req.params); res.end();
})
```
- Here, username can be 'thor' `/thor/message` or `odin` '/odin/message'.
- Now, we can dynamically change URL according to conditions.
## Query Parameters
- Query parameters are a flexible, optional way to pass additional information to your Express application via the URL. 
- They typically handle tasks like filtering, sorting, searching, or pagination. 
- After the query is entered, Devs can then arrange the data recieved according to queries(like sort: ascending etc.).
- `/api/posts?sort=date&time=latest`.
- In this each query is a key-value pair and in format `key=value` and each query is seperated by `&`.
- Express automatically parses any query parameters in a request and will populate the `req.query` object with any key-value pairs it finds. If any keys are repeated, Express will put all values for that key into an array.
- NOTE: HERE `app` IS OUR SERVER!!

# Routers
- Now routers are simple mini-application that handles routes(like `/username/get` or `/username/post`).
- Now we need a dedicated file in which all routes are defined, so we can access all routes from one place, So we create a folder name `routes`
-  
```
// routes/authorRouter.js
const { Router } = require("express");

const authorRouter = Router();

authorRouter.get("/", (req, res) => res.send("All authors"));
authorRouter.get("/:authorId", (req, res) => {
  const { authorId } = req.params;
  res.send(`Author ID: ${authorId}`);
});

module.exports = authorRouter;

```
- Alr, In above code we are getting an 'Router' factory function from express, It's necessary because we can implement the Routing mechanism.
- Now we will destructure Router out of the express package (`const { Router } = require("express")`), and then we called/instantiated it to create our authorRouter (`const authorRouter = Router()`)..
- After that, we will write our function(get or post) and our route('/:authorId').
- Now in the `/:authorId` part, we stored the entered parameter in `authorId` variable, Now we can use `res.send()` to display appropriate message.
- `res.send()` is a built-in method used to send response back to whoever made the request(like web-browsers)
- Now after putting all routers into one place, we can use them as follows
-  
```
// app.js
const express = require("express");
const app = express();
const authorRouter = require("./routes/authorRouter");
const bookRouter = require("./routes/bookRouter");
const indexRouter = require("./routes/indexRouter");

app.use("/authors", authorRouter);
app.use("/books", bookRouter);
app.use("/", indexRouter);

const PORT = 3000;
app.listen(PORT, (error) => {
  if (error) {
    throw error;
  }
  console.log(`My first Express app - listening on port ${PORT}!`);
});
```
- We specify that any requests with paths starting with `/authors` will be passed through `authorRouter` for route matching. If our request starts with `/books`, it will skip these author routes and then check the routes in `bookRouter` instead. Any other requests that don’t start with either of these will run through `indexRouter`.