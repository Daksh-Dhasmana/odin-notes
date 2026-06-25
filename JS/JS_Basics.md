# JavaScript Basics

## JavaScript Arrow Function
-   The industry-standard to define a function is doing it by using Arrow Function
- NOTE: they cannot be used for constructors. Use default
- const <function_name> =(<parameter>)=>{actual code}.
- Eg: const addi=(a,b)=>{return a+b;};

## Why Arrow functions are different from Normal function
- Syntax: Arrow functions give you that sleek, short, one-liner code.
- Behavior: Normal functions have a flexible this (changes based on who calls it), while arrow functions have a locked-down this (stolen from where it was written and locked forever).

## This Keyword
- syntax: `this`.
- this is a keyword that acts like a pronoun. It points to whichever object currently owns or is running the code.
- It lets you write a function once and reuse it across many different objects, while letting those objects read their own internal data.

## How this is Decided (The 4 Quick Rules)
- For a normal function, this looks at how it was called:
    Out in the open: this = the global Window.
    Attached to an object (obj.method()): this = the object to the left of the dot.
    Forced (.call(), .bind()): this = whatever object you manually force into the brackets.
    With new: this = a brand new, empty object created on the spot.
- An arrow function ignores all 4 rules completely.
Instead of looking at who called it, it looks outside of itself, grabs the this value from its parent environment, and locks it in forever.

## Appending HTML tags/content using JS
- // 1. Select the parent element where you want to add the new content
`const container = document.querySelector('#my-container');`

// 2. Create the new HTML tag
`const newParagraph = document.createElement('p');`

// 3. Add text content or attributes to it
`newParagraph.textContent = 'This is a brand new paragraph!';`
`newParagraph.classList.add('highlight-text');`

// 4. Append it to the container
`container.append(newParagraph);`

- If we wanna append an image
`const newImage = document.createElement('img');`
`newImage.setAttribute('src', 'https://example.com/photo.jpg');`
`newImage.setAttribute('alt', 'Descriptive text');`
`newImage.setAttribute('data-id', 'user-123'); // Custom data attribute`