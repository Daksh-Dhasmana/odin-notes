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