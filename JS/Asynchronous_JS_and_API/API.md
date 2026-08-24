# Application Programming Interface(API)
- An API (Application Programming Interface) is a messenger that takes your request to a system, tells the system what you want, and then brings the response back to you.
- For the most part, APIs are accessed through URLs, and the specifics of how to query these URLs change based on the specific service you are using.
- The specifics for using any API are usually documented on the service’s website.
- In most cases, you have to create an account and request for an "API Key" from API service before attempting to use it's services.
- An API Key is random and unique to you.
- Issuing API keys allows an API service to better track abuse of their systems and data. Additionally, it can also be a way for those services to mitigate and recuperate operating costs.
- After all running API costs, it might not cost much to make a single request, but imagine thousands of people using your website making 1000s requests per minute, thus cost can balloon over.
- Thus, you’ll find that most API services, if not all, provide paid tiers that come with the ability to make more frequent requests, or provide access to more information unavailable in lower tiers.
- NOTE: It is IMPORTANT to secure your key, because people might steal your key and use the services YOU paid for!!.

# Fetching Data
- Getting data from API into our code.
- To get data from API we are gonna use fetch
- Syntax:
```
// URL (required), options (optional)
fetch('https://url.com/some/url')
  .then(function(response) {
    // Successful response :)
  })
  .catch(function(err) {
    // Error :(
  });
```

- `fetch()` is a built in JS function that sends a HTTP request to link you provided. By default, fetch() immediately returns a promise.
- `.then()` is a method that waits for Promise to resolve successfully.
  - response object: The server's answer's is passed into function as response package
        - NOTE: To actually read the data, you need to parse it first as it doesn't have the raw JSON, we can parse it using `return response.json()`
- For GIPHY, the url looks like this `'https://api.giphy.com/v1/gifs/translate?api_key=YOUR_KEY_HERE&s=cats'`

- To get the particular details you want, write `console.log(response)` like below
```
fetch('API')
        .then(function(response){
          return response.json();
    })
    .then(function(response){
      console.log(response);    
    })
```

# Including an identification header
- Some APIs might require clients to identify their traffic. When this is the case, you can do it by including a custom identifier header, such as a `User-Agent` or any other identifier the API owner specifies inside the request options
```
const image = document.querySelector("img");
fetch("https://picsum.photos/v2/list", {
  headers: {
    "User-Agent": "the-odin-project"
  }
})
  .then((response) => response.json())
  .then((response) => {
    image.src = response[0].download_url;
  })
  .catch((error) => console.error(error));
```