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
- `// URL (required), options (optional)`
`fetch('https://url.com/some/url')`
  `.then(function(response) {`
    `// Successful response :)`
  `})`
  `.catch(function(err) {`
    `// Error :(`
  `});`
- 
- For GIPHY, the url looks like this `'https://api.giphy.com/v1/gifs/translate?api_key=YOUR_KEY_HERE&s=cats'`