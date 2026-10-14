# Axios
- Axios is a popular open-source JavaScript library used to make HTTP requests from web browsers or Node.js environments.
- Unlike fetch, Axios is a 3rd party.
- Axios and `fetch` do the same tasks but Axios is better than `fetch`.

- NOTE: NEVER LEAVE AXIOS OUTSIDE IN OPEN, always wrap it inside a `useEffect` or something else 

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

  - For more info. [Read the GFG article on axios](https://www.geeksforgeeks.org/html/what-is-axios/ )
- Here's a code on how we use axios to fetch data from a server and display it on website using React component.

## Getting Data from server
-  
```
import React, { useEffect, useState } from 'react'
import axios from 'axios'

const Disp = () => {
    const [persons,setPerson]= useState([]);
    useEffect(()=>{
        axios.get('http://localhost:3001/persons')
            .then(response=>{
                setPerson(response.data)
            })
    },[])
  return (
    <div>
        <ul>
            {persons.map(person=>(
                <li>
                    Person's Name: {person.name};
                </li>
            ))}
        </ul>
    </div>
  )
}

export default Disp
```
- In above code, using `axios.get`, we are fetching data from a server and then axios returns a promise, and if it's successfull then `setPersons` attaches the entire array to `person`.

## Posting Data to server
-  
```
import React, { useEffect, useState } from 'react'
import axios from 'axios'
const Disp = () => {
    const [persons,setPerson]= useState([]);
    const [stat,setStat]=useState("");
    const postData=event=>{
        const newNote={
            "name":"daksh",
        }
        axios.post('http://localhost:3001/persons',newNote)
            .then(response=>{
                console.log(setStat("Completed successfuly"));
            })
            .catch(error=>{
                console.log(setStat("error"));
                
            })
    }
  return (
    <div>
        <button onClick={postData}>Send Data</button>
        <ul>
            {persons.map(person=>(
                <li>
                    Person's Name: {person.name};
                </li>
            ))}
        </ul>
        <p>Result: {stat}</p>
    </div>
  )
}

export default Disp
```
- In above code,This section initializes your component's state using `useState` to track the person records and status messages, and defines the `postData` function which sends a new data object to your local server using `axios.post`, updating your status text depending on whether the network request succeeds or fails.
- You should `event` only when:
  - When stopping a form refresh (`onSubmit`)
    - You need `event.preventDefault()` to stop the browser from reloading the page and wiping out your React state.
  - When reading typed input (`onChange`): 
    - You need `event.target.value` to grab the exact text a user is typing into an input field.