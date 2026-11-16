# Brief refresh on HTML Form
- Let's take a example
-  
```
<form action="/create" method="POST">
  <label for="fullName">Full Name:</label>
  <input placeholder="John Doe" type="text" name="fullName" id="fullName">
  <button type="submit">Submit</button>
</form>
```
- `action="/create"`
  - Specifies the destination URL path (the route) where the browser will send the form data when the user clicks submit. In your Express backend, you will need a matching route handler (like `app.post('/create', ...`)) to catch this request.
- `method="POST"`
  - Defines the HTTP method used to send the data. Using POST means the form data is safely bundled up inside the HTTP request body (hidden from the URL), which is the standard way to create or save new data to a database.
- `for="fullName"`
  - What it does: Connects this text label directly to the input field that has the matching id.
  - Why it's useful: If a user clicks on the text "Full Name:", the browser will automatically focus the cursor inside the input box. It also helps screen readers for accessibility.
- `type="text"`
  - What it does: Tells the browser what kind of input field to render. Setting it to "text" creates a standard single-line text box where the user can type letters, numbers, or symbols.
- `id="fullName"`
  - What it does: Gives this specific HTML element a unique identifier on the page. It is used here to link with the <label>'s for attribute, and it's also what frontend JavaScript or CSS selectors use to target this exact element.
- `name="fullName"`
  - What it does: This is arguably the most important attribute for your backend! The name acts as the key when the form data is submitted. When Express receives this request, req.body.fullName will contain whatever the user typed into this box. (Without a name attribute, the server receives the value, but has no key name to identify it).

# Validation and Sanitation
- Now before we send any data, there are 2 steps that are importand: Validation, Sanitation
  - Validation:- Ensures that user meets specified criteria(required fields, correct formats etc.)
  - Sanitation:- Cleans user input to prevent malicious data from being processed by removing or encoding potentially malicious characters.

# Express-Validator
- Now, to do Validation and Sanitation, we will use `express-validator` which is also the industry standard for validation and sanitation.
- Here's the thing, HTML/React sends form data to express and then express uses express-validator to validate that data.
- Install it using: `npm install express-validator`
- To start using the package, we have to "require" it first in our project `const { body, validationResult } = require("express-validator");`
## Body() Function
- The body() function allows you to specify which fields in the request body should be validated and sanitized, as well as how to handle it. Let's take a look at example below.
-  
```
[
  body("birthdate", "Must be a valid date.")
    .optional({ values: "falsy" })
    .isISO8601() // Enforce a YYYY-MM-DD format.
];
```
- In above code, `birthdate` field is marked as optional but still enforces the ISO8601 date formats on input.
- the `optional({ values: "falsy" })` tells the operator that is field is optional and `values:falsy` means if the user leaves the field empty, sends an empty string `""`, `null`, `undefined`, or `false`, `express-validator` will simply skip the remaining validation rules and let it pass without throwing an error.
- NOTE: You can also chain multiple validation methods.