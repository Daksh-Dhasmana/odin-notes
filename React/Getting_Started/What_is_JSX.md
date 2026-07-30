# What is JSX
- JSX is a syntax extension for JavaScript that lets you write HTML-like markup inside a JavaScript file. It’s not required to use JSX when writing React components, but it does make writing them more concise.
- Instead of making you write messy JavaScript functions, React lets you write HTML-like code inside JS. That HTML-like code is JSX.
  
# Why do we need JSX
- Previously, we separated code by file type (.html and .js), even though the logic and layout were tightly coupled.
- Let's take an example
  - assume you are creating a button feature in which when you click it, it changes the background color of button
  - Now previously, we create 2 files for this, `index.html` and `script.js`, we create id, attribute and button tag in `index.html` and the logic in `script.js`, now this is just 1 feature, imagine you have multiple features that are spread across `index.html` and `script.js`, this can be.. difficult to manage
  - So React offers up a solution, we can do it in a single `.jsx` file, like creating and writing logic for the button in a single `.jsx` file
  
# Rules of JSX

**1) Return a single root element**
   - If you wish to return multiple elements in a component, you can do so by wrapping them in a parent tag
   - This can be a `<div>`, or, if you don’t want the elements to have a container, you could use a React fragment, like so: <>Children</> or just <>..</> 
    ```
    function App() {
        // Could replace <></> with <div></div>
        return (
            <>
                <h1>Example h1</h1>
                <h2>Example h2</h2>
            </>
        );
    }
    ```
  -  Use `<>` (Fragment) when you are only grouping elements to satisfy React's "one root element" rule, and you don't need to apply any CSS classes, click handlers, or layout styling to that wrapper.
  - Use `<div>` when you actually need a physical container on the screen—like when applying CSS flexbox, grid, padding, background colors, or border styling.
  
**2) Close all tags**
- In JSX, we must explicitly close and wrap these tags.
- like `<input>` becomes `<input />` and `<li>`  becomes `<li></li>`

**3) camelCase Most things.**
- camelCase is a way of naming things in programming where you combine multiple words into a single word without spaces, keeping the first word entirely lowercase and capitalizing the first letter of every word after it.
- JSX turns into JavaScript, and attributes of elements become keys of JavaScript objects, so you can’t use dashes or reserved words such as class. 
- Because of this, many HTML attributes are written in camelCase. Instead of `stroke-width`, you’d use `strokeWidth`, and instead of `class` you’d use `className`.

