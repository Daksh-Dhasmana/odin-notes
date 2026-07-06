# Introduction
- Since JavaScript is the language of the web, there are some functions that by necessity are going to take a decent amount of time to complete, such as fetching data from a server to display on your site. For this reason, JavaScript includes support for asynchronous functions, or to put it another way, functions that can happen in the background while the rest of your code executes.

# Callback
- Callbacks are functions that are passed as arguments from one function to another and are executed after the completion of a certain task. 
- A callback function is simply a function you hand over to another function, to be run later.
- They are commonly used in asynchronous operations, such as reading files, making HTTP requests, or handling user input.

## Callback Hell
- Callback Hell in JavaScript can be defined as the situation where we have nested callbacks(functions passed as arguments to other functions) which makes the code difficult to read and debug. 
- The term "callback hell" describes the deep nesting of functions that can result in poor code readability and difficulty in debugging, especially when handling multiple asynchronous operations.
- Suppose you are making a Pizza, so you have to do it in 3 steps;
   - Prepare the Dough
   - Add Toppings
   - Bake the pizza
- You can't bake pizza without preparing the dough, so what does callback hell does is that it gives a instruction/step on how to do it
- `prepareDough(function() {`
    `addToppings(function() {`
        `bakePizza(function() {`
            `console.log("Pizza is ready!");`
        `});`
    `});`
`});`
- In above, what we essentially are telling that, prepare the dough first then add toppings and then bake pizza, and this complicates things as it become hard to read and debug


## Solution to Callback Hell

### Promises
- Promises can help in avoiding the callback hell by providing the structured way to handle the asynchronous operations using the .then() method.
- Instead of nesting functions inside each other like Russian dolls, a Promise allows you to attach .then() to the end of a function. It literally reads like a timeline: "Do this, then do that, then do that."
- a Promise is an object representing the eventual completion (or failure) of an asynchronous operation.

#### 3 Stages pf promise
- 1st State: Pending
        - Meaning: the asynchronous operation is still working. It hasn't succeeeded or failed yet.
        - What Happens next: It waits.
- 2nd State: Fulfilled
        - Meaning: The operation completed successfully
        - What Happens next: The `.then()` block is triggered
- 3rd State: Rejected
        - Meaning: The operation failed (e.g., network error, file not found).
        - What Happens next: The `.catch()` block is triggered.

- Syntax:
- `let promise = new Promise((resolve, reject) => {`
    `// Perform async operation`
    `if (operationSuccessful) {`
        `resolve("Task successful");`
    `} else {`
        `reject("Task failed");`
    `}`
`});`
- resolve(value): Marks the promise as fulfilled and provides a result.
` reject(error): Marks the promise as rejected with an error.

- Let's take the above example of Baking pizza, we can use promises to make it clean.
`function prepareDough() {`
`    return new Promise((resolve) => {`
`        console.log("Starting dough...");`
`        setTimeout(() => {`
`            console.log("Dough is ready! 🌾");`
`           resolve();`
`        }, 2000);`
`    });`
`}`
``function addToppings() {` 
`    return new Promise((resolve) => {` 
`        console.log("Adding toppings...");` 
`        setTimeout(() => {` 
`            console.log("Toppings are on! 🍕");` 
`            resolve(); ` 
`        }, 1500);` 
`    });` 
`}`
`function bakePizza() {`
`    return new Promise((resolve) => {`
`        console.log("Baking pizza...");`
`        setTimeout(() => {`
`            console.log("Baking finished! 🔥");`
`           resolve();`
`        }, 3000);`
`    });`
`}`
``
`prepareDough()`
`    .then(() => {`
`       return addToppings();`
`    })`
`    .then(() => {`
`       return bakePizza();`
`    })`
`    .then(() => {`
`        console.log("Pizza is ready! 🎉 Enjoy your meal.");`
`    })`
`    .catch((error) => {`
`        console.error("Oh no, something went wrong making the pizza:", error);`
`    });`
- `.then()` is a listener that only runs if the Promise successfully called resolve().
- `.catch()` is a listener that only runs if the Promise failed and called reject(). 

