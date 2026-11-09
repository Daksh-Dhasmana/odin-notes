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
  - Specifies the destination URL path (the route) where the browser will send the form data when the user clicks submit. In your Express backend, you will need a matching route handler (like app.post('/create', ...)) to catch this request.
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