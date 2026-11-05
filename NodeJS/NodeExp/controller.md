# Controller
- It's like the ulimate middleman.
- It doesn't build the site(like React/HTML), It doesn't stores info(Like mongoDB)
- It mearly connects them so they can communicate.
- Controller is a concept

## Handling Responses
- Now we have to send responses from our controller
- There are some commonly used methods and below are there use cases.
1) `res.send` 
      - A general purpose method for sending responses.
      - It is quite flexible as it changes it's `Content-Type` based on data we will send.
      - If data to be sent is JSON, then `Content-Type` will set to `application/json`.
2) `res.json`
      - As name suggests this will send data as JSON
      - This is more explicit way to respond a request with JSON.
      - This always sets `Content-Type` to `application/json`.
3) `res.redirect`
      - This will redirect the client to a different URL.
4) `res.render`
      - It is used to send fully rendered HTML webpage to browser.
      - It is strictly meant for traditional Server-Side Rendering (SSR) using template engines like EJS, Pug, or Handlebars, where the server builds the HTML page and sends it to the browser.
      - REACT WILL NOT WORK! ONLY HTML!!
5) `res.status`
   - It is a method used to set the HTTP status code of the response before you send it back to the client. 
   - By default, when you use `res.send()` or `res.json()`, Express automatically sends a 200 OK status code. 
   - You use `res.status()` when you need to change that code to indicate success, error, or redirection.
   - Now, the question arises "if we cannot display error codes to browser, why do we need it at all?"
   - The answer is quite simple:- Frontend Logic(React) uses the sent status code, to determine what to display
   - For eg: controller sends this code to frontend`return res.status(404).json({ message: "Item not found" });` and then upon recieving it frontend can use it to determine what content to display, like this
   -  
```
if (response.status === 404) {
        console.log("Trigger error: Display a 'Not Found' popup to the user.");
    } else if (response.ok) { // 200-299 range
        const data = await response.json();
        console.log("Success: Render the item on the screen.", data);
    }

```
- NOTE: sending a response method like `res.send` and `res.json` end only [request-response cycle](./ReqResCycle.md) and function still continues to operate further on

## Middleware
- They are a core concept in Express and play a crucial role in handling requests and responses.
- A middleware argument takes 3 argument
- `req` - The request object, representing the incoming HTTP request.
- `res` - The response object, representing the HTTP response that will be sent back to the client.
- `next` - The function that passes control to the next middleware function in the chain (we’ll get to this later). This is optional.
- A middleware function can perform various tasks, such as:
  - Modifying the request or response objects (some packages for example will do this, like adding a new property in the request object, or setting the res.locals that is used in templates rendered with res.render).
  - Executing additional code (validation middleware functions to validate the request before going to our main logic, authentication middleware functions, and so on).
  - Calling the next middleware function in the chain.
  - Ending the request-response cycle (meaning no further middleware functions are called, even if there are more in the chain).

## Application-level Middleware
- It is directly bound to an Express instance and applies globally.
- We typically denote it using app, like `const app = express();`.
- Express executes these middleware functions for every incoming request that matches the specified path. 
- If we don’t specify a path, Express defaults the path to /, matching every incoming request. 
- As with any middleware functions, they will not run if the request-response cycle ends before reaching them. 
- Typically, these middleware functions are placed on top of our application code to ensure they always run first.
- Express also gives several essential built-in functions for middleware like:
  - Body Parsers(express.json()), These allow us to correctly parse the incoming request’s body, so that we can use it through req.body.
  - Serving static files(eg: `app.use(express.static('public'))`)
    - Serving static files is the direct transmission of unchanged assets (such as CSS, images, and frontend scripts) from server storage to the client browser without backend execution.
    - Express automates this process using the `express.static()` middleware, which maps a specified local directory directly to public URL endpoints.
    - This eliminates the need to write manual route handlers for every individual file, allowing browsers to fetch assets via standard HTTP requests.

## Router-Level Middleware
- It is similiar to application-level middleware but it is bounded to Express Router using `router.use` or `router.METHOD` functions.
- Because of this, Express only executes these middleware when the request matches and goes through that router.

## Q) Is the `app` and `router` same? since both of them do same task?
- They both do same task of route matching and HTTP matching, so in which way do they differ?
- Think of `app` as the manager and `router` as sub-module, They indeed do same task but `app` oversees the whole application and `router` oversees the sub-division
- Here how it happens
  - **The Request Arrives**: A client sends a POST request to `http://localhost:3000/api/users/42/posts`.
  - **`app` Catches It First**: Because app is the master container running the server port (`app.listen`), it receives the raw network request.
  - **The Prefix Match (`app.use`)**: app looks at its registered middleware and sees this line of code: `app.use('/api/users', userRouter);`, `app` checks if the incoming URL starts with `/api/users`. Because it does, `app` strips away that prefix and hands the remaining piece (`/42/posts`) over to the `userRouter`.
  - **`router` Takes Ove**r: The `userRouter` now processes that remaining piece (`/42/posts`), matches it to its internal definition (`/:id/posts`), and executes the controller logic to handle the post.
  - Here's a code:
  - 
```
// routes/users.js
const express = require('express');
const router = express.Router();

// The router receives the stripped path ('/42/posts') and matches it here:
router.post('/:id/posts', (req, res) => {
    // req.params.id captures "42" from the URL
    const userId = req.params.id; 
    
    // req.body captures the payload sent in the POST request
    const postContent = req.body;

    res.status(201).json({
        success: true,
        message: `Post successfully created for user ID: ${userId}`,
        receivedData: postContent
    });
});

module.exports = router;
```
- 
```
// server.js
const express = require('express');
const app = express();

// 1. Global middleware to parse JSON bodies in POST requests
app.use(express.json());

// 2. Import the user router module
const userRouter = require('./routes/users');

// 3. The handoff point: 
// When a request comes in for "/api/users/42/posts", 
// app catches it, strips "/api/users", and passes "/42/posts" to userRouter.
app.use('/api/users', userRouter);

// 4. Start the server (Only `app` can do this)
app.listen(3000, () => {
    console.log('Server is running on port 3000');
});
```

# Controller
- A controller is just the function that handles the actual work for a specific route.
- It is a core concept in [MVC(Model-View-Controller)](./mvc.md)
- Every single piece—parsers, loggers, auth checks, and route dispatchers—is just middleware sitting in a pipeline, inspecting the request, processing it, and finally handing it off to the correct controller to finish the job.
- In short, middleware takes the request and then it selects the appropriate controller to handle the req.
- The Router (or route matcher) is what maps the URL path and decides which controller to call.
- The Controller is the actual function that runs when that route is matched
- Pipeline flows like this: Request -> Middleware (parsers, auth) -> Router (matches path) -> Controller (executes logic & responds).