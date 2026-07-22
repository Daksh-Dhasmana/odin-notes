# JSON
- Also known as JavaScript Object Notation.
- Is a format for structuring data as plain text. or represents structured data as a string
- For example: 
    - Your application takes complex data and turns it to flat JSON text string and send
    over the internet.
    - The receiving application reads JSON text and rebuilds it into usable data.
- Used commonly for APIs and config
- Integrates with most language.
- We have to write it in key value pairs.
- There are 4 types of jSON: numbers, bool, string and objects
- eg:
 ` {`
    `"name":"daksh",`
    `"programmer":true,`
    `"favouriteNumber":10,`
    `"friends":{`
        `"name":"aksh",`
        `"name":"akash",`
        `"name":"akshay"`
    `}`
 `}`

# JSON.parse()
- A common use of JSON is to exchange data to/from server.
- When recieving the data from server, the data is a string.
- Parse the data with JSON.parse(), the data becomes a JavaScript object.
- Eg: 
    - we recieve this data/text from server.
      - `{"name":"John", "age":30, "city":"New York"}`
    - use JavaScript function JSON.parse() to convert it into JS Object.
      - `const obj = JSON.parse('{"name":"John", "age":30, "city":"New York"}');`
- NOTE: Make sure text is in JSON format, or else we will get syntax error.

# JSON.stringify()
- It works exactly the opposite of `json.parse()`
- eg: 
    - suppose we have this object in JS `const obj = {name: "John", age: 30, city: "New York"};`
    - Using JS function `json.stringify()` to convert it into string `const myJson=JSON.stringify(obj)`
    - now myJson is now a string and ready to be sent to server
    
