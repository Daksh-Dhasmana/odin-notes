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