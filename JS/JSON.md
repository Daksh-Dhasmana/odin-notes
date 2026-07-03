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

# Converting between objects and texts
- There are two methods for this:
   - `parse()`: Accepts JSON as a parameter and returns corresponding JS object.
   - `stringify()`: Accepts object as a parameter and returns equivalent JSON string.