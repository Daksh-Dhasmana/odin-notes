# What is State in React
- State is a plain JavaScript object or primitive value that represents a component's memory. 
- It holds data that can change over time based on user interactions, network responses, or timers, and directly influences what appears on the screen.
- When a component's state changes, React automatically re-renders that component to update the UI to match the new state.

## Key Components
  - Component Memory: 
    - Unlike standard variables (which reset every time a component re-renders), state variables persist across re-renders.
  - Triggers Re-renders: 
    - Modifying state using its setter function tells React that the component needs to be re-drawn on the screen.
  - Immutability: 
    - You should never update state directly (e.g., count = 5). Instead, always use the state updater function provided by React to ensure re-renders are triggered correctly.
  
# What is Hooks
- In React, Hooks are functions that let functional components "hook into" React features—such as state management and lifecycle methods—without writing class components.

## Commonly used Hooks are
- useState (State Management)
  - Allows functional components to store and update internal stat
- useEffect (Side Effects)
  - Handles side effects like fetching data, directly manipulating the DOM, setting up timers, or subscribing to external events. 
  - It replaces class lifecycle methods like componentDidMount, componentDidUpdate, and componentWillUnmount.

# How to structure State
- Managing and structuring state effectively is by far one of the most crucial parts of building your application. If not done correctly, it can become a source of bugs and headaches.
- As a general rule of thumb: don’t put values in state that can be calculated using existing values, state, and/or props. Like name

## States should not be mutated
- According to the React documentation, we should treat state as if it was immutable. To change state, we should always use the `setState` function,which in the case of the example below is the `setPerson` function.
```
function Person() {
  const [person, setPerson] = useState({ name: "John", age: 100 });

  // BAD - Don't do this!
  const handleIncreaseAge = () => {
    // mutating the current state object
    person.age = person.age + 1;
    setPerson(person);
  };

  // GOOD - Do this!
  const handleIncreaseAge = () => {
    // copy the existing person object into a new object
    // while updating the age property
    const newPerson = { ...person, age: person.age + 1 };
    setPerson(newPerson);
  };

  return (
    <>
      <h1>{person.name}</h1>
      <h2>{person.age}</h2>
      <button onClick={handleIncreaseAge}>Increase age</button>
    </>
  );
}
```
- In the above example, notice how we create a new object and then copy the existing state values into the new object while providing a new value for age. That is because if we don’t provide a new object to `setState` it is not guaranteed to re-render the page. Therefore, we should always provide a new Object for `setState` to trigger a re-render. `setState` uses `Object.is()` to determine if the previous state is the same.
- Above rule only applies, Only if the thing you are changing is an Object or an Array.

## How States changes
- States updates are asynchronous, What this implies is that whenever you call the setState function, React will apply the update in the next component render.
- States variables are not reactive, but the component is, meaning, calling the `setState` renders the entire component instead of changing the variables.

# Controlled Components
- It is a form whose input field value is controlled by React's State
- Here's how it works
  - Store input field value in State
  - Use onChange handler with i/p field
  - Value attribute attached with state
- eg:
```
import { useState } from "react";
import React from "react";
function App() {
  const [name, setName] = useState("");
  const [pass, setPass] = useState("");
  
  return (
    <>
    <input type="text" value={name} onChange={(e)=>setName(e.target.value)}/> 
    <br/>
    <input type="text" value={pass} onChange={(e)=>setPass(e.target.value)}/> 
    <br/>
    <h1>{name}</h1>
    <h2>{pass}</h2>
    <button onClick={()=>{setName("");setPass("")}}>Clear</button>
    </>
  );
}
export default App;
```
- here, `value={name}`, it will show what you write, inside the inputbox
- `onChange={(e) => ...}`, it will listen to your typing, a letter, delete a letter etc.
- `e.target.value` (Getting the new text)
  - `e.target` = The input box itself.
  - `e.target.value` = Whatever text is inside the input box right now.
  - `setName(e.target.value)` = Takes that new text and updates the name state variable
## Benefit of Controlled Components
- Single Source of truth
- Validation and Manipulation before Submit
- Dynamic updates values