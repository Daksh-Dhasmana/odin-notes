# How to install React

## Step 1
- Open The VScode terminal

## Step 2
- Initialize Vite
- In the terminal run
- `npm create vite@latest .`

## Step 3
- Select your options
- Use your keyboard arrow keys and Enter to make the following choices when prompted:
1) Package name: Press Enter (defaults to current folder).

2) Select a framework: Choose React

3) Select a variant: Choose JavaScript (or JavaScript + SWC / TypeScript depending on your preference).

4) Which linter to use? Choose ESLint

## Step 4 
- Install dependencies including react itself
- Run the command
- `npm install`

## Step 5
- Start Local Server
- `npm run dev`
---

- The `public` folder is where all of the static assets related to your app will go. This could include images, icons, and information files for the browser.
- Inside the src folder is where you will find the code that runs your app. The main.jsx file here serves as the entry point of the application.
- Inside the `main.jsx` file you will find the following code
```
import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import App from "./App.jsx";
import "./index.css";

createRoot(document.getElementById("root")).render(
  <StrictMode>
    <App />
  </StrictMode>,
);
```
- Here's a brief rundown
- 1) We import `StrictMode` and `createRoot` from the `react` and `react-dom` packages respectively.
- 2) We import the `App` component from `App.jsx`, so that we may place (render) it within the DOM.
- 3) We import some CSS styling (you may recognize this syntax from the Webpack material).
- 4) We create a `root` object by invoking `createRoot` with an element from our `index.html`.
- 5) We invoke the `render` method, which is attached to our `root` object, with some very interesting-looking syntax inside the parentheses.

- **NOTE**: YOU DO NOT NEED TO CREATE A NEW .HTML FILE AS ONLY INDEX.HTML FILE WILL SUFFICE