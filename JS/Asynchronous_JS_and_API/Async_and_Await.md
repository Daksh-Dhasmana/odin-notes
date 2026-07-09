# Async Keyword
- It is a keyword is modifier that signals that the function is an asynchrous function and will handle asynchrous operation/s.
- We place it right before a function declaration.
- It does 2 important things:
      - Unlocks `await`: It tells the engine that this function is allowed to pause execution mid-way using `await` keyword.
      - Guarantees a Promise: It always forces the function to return a promise
  
# Await Keyword
- We use `await` right before a asynchronous operation like fetch.

- NOTE: An asynchronous function is a special type of JavaScript function that allows you to kick off a long-running background task—like fetching data from an API or reading a massive file—without freezing the rest of your application.
- If you don't use async/await, JavaScript will aggressively rush past your API call without waiting for the data; if you do use async/await, you are forcing JavaScript to cleanly pause inside that function until the data is safe in your hands, while the rest of the webpage runs completely as normal.
- BEFORE:
    `// NO ASYNC/AWAIT`
`console.log("1");`
`fetch('https://api.com/data'); // Fires off in background, takes 3 seconds`
`console.log("2"); // Runs INSTANTLY (0.001 seconds later). It didn't wait for the fetch!`

- AFTER: 
    `// WITH ASYNC/AWAIT`
`async function getData() {`
  `console.log("1");`
  `await fetch('https://api.com/data'); // 🛑 Function execution PAUSES here for 3 seconds!`
  `console.log("2"); // Waits 3 seconds to run.`
`}`

# Error Handling
- There are actually 2 methods for error handling in async functions.
  - try and catch
  - .catch method

## Try and catch
- It works like any other try and catch
`async function getPersonsInfo(name) {`
  `try {`
    `const people = await server.getPeople();`
    `const person = people.find(person => { return person.name === name });`
    `return person;`
  `} catch (error) {`
    `// Handle the error any way you'd like`
  `}`
`}`

## .catch method
- .catch method is used to handle rejected promises.
- Syntx: 
`asyncFunctionCall().catch(err => {`
  `console.error(err)`
`});`

- Use below code 
  `async function getWeatherData(cityName) {`
  `// 1. Define your API URL (usually with your API key and search parameters)`
  `const apiKey = "YOUR_ACTUAL_API_KEY_HERE";`
  `const url = `https://api.weatherapi.com/v1/current.json?key=${apiKey}&q=${cityName}`;`

  `try {`
    `// 2. Await the initial network request`
    `const response = await fetch(url);`

    `// 3. Check if the network request actually succeeded (e.g., city found, 200 OK)`
    `if (!response.ok) {`
      `throw new Error(`HTTP error! Status: ${response.status}`);`
    `}`

    `// 4. Await parsing the response body into usable JSON data`
    `const data = await response.json();`
    
    `// 5. Return the final data object`
    `return data;`

  `} catch (error) {`
    `// Handle network errors, typos in URL, or issues thrown above`
    `console.error("Failed to fetch weather data:", error);`
  `}`
`}`
