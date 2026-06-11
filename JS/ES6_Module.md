# Modules
- an ES6 Module is just a JavaScript file that can share its code with other JavaScript files.
- Modules are used to divide the code into multiple files for organization.

## Export and Import
- for exporting we use `export` keyword and `import` keyword
- There are two types of importing and exporting: Default and named.
- Go with Named Exports when building utility files, math/helper functions, configuration sets, or when you are working on a strict team that demands absolute naming consistency.
- Go with Default Exports when a file is meant to be an isolated standalone module (like a single UI component or a core class blueprint) that has one clear responsibility.
- Default, eg: - eg: `export { greeting, farewell };`
      `import { greeting, farewell } from "./one.js";`.

# Entry point
- An entry point is the primary JavaScript file where a program or application starts execution and kicks off the entire module dependency chain.
- if `two.js`<---`one.js`<--`three.js`, then two is the entry point
- syntax `<script src="two.js" type="module"></script>`

# Dependency Graph
- A dependency graph is a visual or conceptual map that JavaScript engines build to track how different code files (modules) connect to, import, and depend on each other.
- When you use import and export statements in your code, you are manually drawing lines between files. The JavaScript engine reads those lines and builds the dependency graph.
