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