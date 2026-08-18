# Introduction to React Testing
- In this, we are gonna learn about Vitest and will switch to Vitest from Jest, since Vitest integrates nicely with vite.
- Then we will add more cabability using React Testing Library(RTL).

# UI Testing
- UI tests give us more confidence that our websites contain the intended contents and behave as we want, and notify us when something no longer satisfies our requirements. 

# Installing Vitest with RTL
- To install, follow the following guide/link
- https://www.robinwieruch.de/vitest-react-testing-library/
- and then install this package
- `npm install @testing-library/user-event --save-dev
`
- In every `.test.jsx` file, import the following thing
```
// Brings in core React features (optional in newer React, but needed for JSX parsing)
import React from 'react';

// Brings in Vitest testing functions like describe (suites), it (tests), and expect (assertions)
import { describe, it, expect } from 'vitest';

// Brings in React Testing Library functions to render components into a virtual DOM and query elements
import { render, screen } from '@testing-library/react';

// Extends Vitest's expect with custom DOM matchers like toBeInTheDocument()
import "@testing-library/jest-dom/vitest"; 

// Imports the actual React component you want to test
import Greeting from './Greeting.jsx';
```
- [CheetSheet](https://testing-library.com/docs/react-testing-library/cheatsheet)
- Above is the cheetsheet for testing

 # Queries
 - Queries are the methods that Testing Library gives you to find elements on the page. 
 - There are several types of queries ("get", "find", "query");
 - The difference between them is whether the query will throw an error if no element is found or if it will return a Promise and retry.
 - After selecting an element, you can use the Events API or user-event to fire events and simulate user interactions with the page, or use Jest and jest-dom to make assertions about the element.
  
## Types of Queries
- **1) Single Elements**
  - `getBy...`: 
    - Returns the matching node for a query, and throw a descriptive error if no elements match or if more than one match is found (use getAllBy instead if more than one element is expected).
  - `queryBy...`: 
    - Returns the matching node for a query, and return null if no elements match. This is useful for asserting an element that is not present. 
    - Throws an error if more than one match is found (use queryAllBy instead if this is OK).
  - `findBy...`: 
    - Returns a Promise which resolves when an element is found which matches the given query. 
    - The promise is rejected if no element is found or if more than one element is found after a default timeout of 1000ms. 
    - is used in React Testing Library when you are waiting for something to appear asynchronously on the screen (like data arriving from an API or a component appearing after a setTimeout).
    - If you need to find more than one element, use findAllBy