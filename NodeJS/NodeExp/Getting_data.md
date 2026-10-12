# Axios
- Axios is a popular open-source JavaScript library used to make HTTP requests from web browsers or Node.js environments.
- Unlike fetch, Axios is a 3rd party.
- Axios and `fetch` do the same tasks but Axios is better than `fetch`.

## Why use Axios instead of `fetch`?
1) Automatic JSON Parsing
    - With `fetch`: 
      - When server sends back the data you have to manually convert it back to .json before reading/accessing it.
    - With Axios: 
      - Automatically parses incoming JSON data and is ready to use.
2) Better Error Handling(Status Code)
   - With `fetch`:
     - When server sends an error message, fetch does not consider it to be a failure, meaning you have to implement if-else chain or then-catch chain to process the error message.
   - With Axiom:
     - Any error status code (like 4xx or 5xx) automatically triggers a rejection, jumping straight into your .catch() block or throwing an error, which matches what most developers intuitively expect. 
3) Cleaner syntax
-  Axiom has cleaner syntax than `fetch`. 