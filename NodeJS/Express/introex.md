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
- `/api/posts?sort=date&time=latest`
