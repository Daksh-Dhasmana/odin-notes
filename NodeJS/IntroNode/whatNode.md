# What is Node
- Node JS website says,"As an asynchronous event driven JavaScript runtime, Node is designed to build scalable network applications."
- Before creation of Node.js in 2009, we could only use JS inside the browser, so Node.js helps bring JS outside the browser environment, so Node.js is not a language it's a Runtime Environment.
- Why do we have to bring JS out of the browser world? because:
  - 1) One Language Everywhere: 
    - Developers write both frontend UI(React is a JS library) and backend APIs using a single language (JS/TS), eliminating the need to learn PHP, Python, or Java for the server.
    - Meaning Devs can write both frontend and backend using JS.
  - 2) Built for High Speed (Non-Blocking I/O): 
    - JS uses an event-loop model that easily handles thousands of concurrent requests (like chats, streams, and real-time APIs) without freezing or using excessive memory.
  - 3) Shared Code & NPM: 
    - Write data validation rules or helper functions once and reuse them across both client and server, backed by the largest package library in the world (NPM).
  - When Node.js performs an I/O operation, like reading from the network, accessing a database or the filesystem, instead of blocking the thread and wasting CPU cycles waiting, Node.js will resume the operations when the response comes back.
  - This allows Node.js to handle thousands of concurrent connections with a single server without introducing the burden of managing thread concurrency, which could be a significant source of bugs.
  - To summarize, Node.js is JS which executes on server.
# Event Driven
- Node is an asynchronous event driven JavaScript runtime. 
- In this context, asynchronous means that when you write your code, you do not try to predict the exact sequence in which every line will run. 
- Instead, you write your code as a collection of smaller functions that get called in response to specific events, such as a network request (event driven).
- Suppose there are multiple processes running like reading file, calling API, what Node.JS does, it starts every process according to order, but which ever process finishes first, it will execute it first

- To run Node.js inside terminal use the following syntax
- `node e "JS code"`
- eg: `node e "console.log("100");`

# Restart the application
-  there is a built-in option to automatically restart the application when a file changes. This is useful for development purposes
-  `node --watch app.js`

- **Q) But we use fetch in both React and Node.js, so when to use what?**
  - We DO use API fetch in both React and Node.js, but for different purposes.
  - React (Frontend / Browser): 
    - Fetches data to display it to the user on their screen (e.g., getting a user's profile to render their avatar).
  - Node.js (Backend / Server): 
    - Fetches data to process it, secure it, or store it before sending it along (e.g., calling a payment system like Stripe to charge a credit card).
  - So, Node.js = V8 JavaScript Engine +C++ Bindings (Operating System Tools)
    - **The V8 JS Engine**: Google Chrome's open-source C++ program that reads your standard JavaScript syntax (variables, functions, arrays, async/await) and compiles it into machine code.
    - **C++ Bindings**: Native C++ libraries (like libuv) built into Node that handle system-level hardware tasks:
      - Accessing the Filesystem (reading/writing files on disk).
      - Managing Network I/O (opening TCP sockets and HTTP server ports).
      - Interacting with the Operating System (checking CPU usage, RAM, environment variables).