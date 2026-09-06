# What is Node
- Node JS website says,"As an asynchronous event driven JavaScript runtime, Node is designed to build scalable network applications."
- Before creation of Node.js in 2009, we could only use JS inside the browser, so Node.js helps bring JS outside the browser environment, so Node.js is not a language it's a Runtime Environment.
- Why do we have to bring JS out of the browser world? because:
  - 1) One Language Everywhere: 
    - Developers write both frontend UI(React is a JS library) and backend APIs using a single language (JS/TS), eliminating the need to learn PHP, Python, or Java for the server.
  - 2) Built for High Speed (Non-Blocking I/O): 
    - JS uses an event-loop model that easily handles thousands of concurrent requests (like chats, streams, and real-time APIs) without freezing or using excessive memory.
  - 3) Shared Code & NPM: 
    - Write data validation rules or helper functions once and reuse them across both client and server, backed by the largest package library in the world (NPM).
# Event Driven
- Node is an asynchronous event driven JavaScript runtime. 
- In this context, asynchronous means that when you write your code, you do not try to predict the exact sequence in which every line will run. 
- Instead, you write your code as a collection of smaller functions that get called in response to specific events, such as a network request (event driven).
- Suppose there are multiple processes running like reading file, calling API, what Node.JS does, it starts every process according to order, but which ever process finishes first, it will execute it first