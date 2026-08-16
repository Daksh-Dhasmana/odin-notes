# Jest
- Jest is a JavaScript testing framework designed to ensure that your code works exactly the way you expect it to.
- It acts as a automatic safety net that checks for bug before it's shipped to production
- But you might think, VSCode also does the same, like highlighting errors in red, so why do we need an whole extra tool like Jest? the difference is that: 
          - VSCode checks the code syntatically meanwhile Jest checks the Logic of code.
          - Jest looks for Logic & Outcomes (Runtime Testing): Jest actually runs your code with real data to see if the math, logic, and business rules work correctly. It ensures your code does what it is supposed to do.
- to install jest use `npm install --save-dev jest`
- By default, the current version of jest wont recogise ESM, so we install babel 
- `npm install --save-dev @babel/preset-env@^7`
- Then create a file by name of babel.config.js in root folder with following code
```
- export default {
  presets: [["@babel/preset-env", { targets: { node: "current" } }]],
};
```
- This will allow you to write ESM’s import/export syntax instead of require/module.exports; you do not need to change anything else in the guide and Jest can be run as normal.
- Behind the scenes, Babel will convert your ESM to CJS before running Jest (it won’t overwrite your actual files as this all happens in memory).
- Add this to package.json
```
- {
  "scripts": {
    "test": "jest"
  }
}
```
- Eg:
- In [file_name].test.js
```
const {sum, capi} = require('./sum');
test('multiplies 3 by 4 to equal 12', () => {
    expect(multiply(3, 4)).toBe(12);
});
```

1) `test('...', () => { ... })`
    - The label "multiplies 3 by 4 to equal 12" is human-readable description. Jest will print this exact sentence out so you know which feature passed or failed.

2) `expect(...)`
    - This is Jest's way of grabbing a value from your application. Inside the parentheses, you call your actual code: multiply(3, 4). Jest runs that function, gets the result (which should be 12), and holds onto it.

3) `.toBe(12)`
    - This is called a Matcher, it connects directly to expect(), it tells to Jest: "Take the result you just got from multiply(3, 4) and check if it is exactly equal to 12."

4) `const {sum, capi} = require('./sum');`
    - here, sum and capi are functions exported from require('./sum.js)
- After all this, run the command `npm test`, which will test it      

## How do we exactly export functions for testing?
- `function sum(a,b){`
    `return a+b;`
`}`
`function capi(str){`
    `return str.charAt(0).toUpperCase() + str.slice(1);`
    `return c;`
`}`
`module.exports={`
    `sum:sum,`
    `capi:capi`
`};`
- Like this.