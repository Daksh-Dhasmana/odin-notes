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