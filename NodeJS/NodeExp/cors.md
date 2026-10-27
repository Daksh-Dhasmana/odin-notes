# Same-Origin Policy(SOP)
- The Same-Origin Policy is a fundamental security mechanism built into all web browsers. It prevents malicious websites from reading sensitive data from another website without permission.

- ## Origin Header
  - Two URLs share the same origin if and only if they have same:
    - Protocol(eg: http and https)
    - Domain/host(eg: example.com and eggs.com)
    - Port(eg: localhost:3000 or localhost:4000)
  - And the Origin Header consists for these 3 stuff
- If any one of them differs, the browser will block the site and consider it "cross-origin".
- For example, your application may use your browser to pull videos from a video platform API, use fonts from a public font library, or display weather data from a national weather database. CORS allows the client browser to check with the third-party servers if the request is authorized before any data transfers.
# Cross Origin Resource Sharing(CORS)
- Since modern web applications often separate the frontend (running on something like `http://localhost:5173`) and the backend (running on `http://localhost:5000`), they naturally violate the Same-Origin Policy.
- CORS is the official workaround. It is an HTTP-header-based mechanism that allows a server to relax the Same-Origin Policy and explicitly tell the browser: "It's safe! Allow this specific outside origin to fetch data from me
- ## How does CORS work exactly?
  - There are 3 steps:
    - ### 1)  Browser add `Origin` header ###
      - The browser adds an origin header to the request with information about the current origin's protocol, host, and port
    - ### 2) Server verifies the request ### 
      - The Backend recieves the request
      - Now the server gets the request and it verifies the Origin, if the Origin is legit/correct, it processes the request, gets the data and sends back an HTTP response and attaches a header `Access-Control-Allow-Origin` and if not, It will block the request.
      - 
      ```
      HTTP/1.1 200 OK
      Content-Type: application/json
      Access-Control-Allow-Origin: http://localhost:3000
      { "id": 1, "name": "Wireless Headphones" }
      ```
      - Server checks the request.
    - ### 3) Browser verifies and shares data ###
      - Here is the big secret: the server always processes the request and sends back the data. However, the browser intercepts the incoming response before your JavaScript can touch it. 
      - The browser looks at the server's `Access-Control-Allow-Origin` header and compares it with your website's origin. If they match (or if it's *), the browser unlocks the response and hands the data to your React code. If they don't match, the browser blocks the data and throws a CORS error in your console.
      - Browser checks the response
- To install cors use `npm install cors`
- take the middleware to use and allow for requests from all origins:
-  
```
const cors = require('cors')
app.use(cors())
```