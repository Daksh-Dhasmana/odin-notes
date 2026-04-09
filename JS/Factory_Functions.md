# Functions created from a function
- we can create functions from a function.
- Instead of writing new functions everytime, we just use a function to create a function for us
- eg
`function makeAddFunction(firstnum){`
  `return function returnfunc(secondnum){`
    `return firstnum+secondnum;`
  `}`
`}`
`const add5 = makeAddingFunction(5);`
`console.log(add5(2)); // 7`

# Closure (IMPORTANT)
- A closure gives inner function access to outer function variable even after outer function is done executing.
- The Syntax always involves a "function within function".
- `function init(){`
`  var name = "Mozilla"; // name is a local variable created by init`
  `function displayName() {`
`    // displayName() is the inner function, that forms a closure`
`    console.log(name); // use variable declared in the parent function`
  `}`
`  displayName();`
`}`
`init();`
- It ensures encapsulation(privacy)
- A Closure occurs when an Outer (Mother) function defines a private variable and returns an Inner (Child) function/s. This pattern creates a Private Scope where the variable is inaccessible to the rest of the program, effectively granting the 'Child' function/s exclusive, persistent access to that data even after the 'Mother' function has finished executing.
  
# Factory Function
- They use the power of closures
- Factory Functions dont need the `new` keyword when creating an object, instead they set up and return a new object when you call the function.
- No need to use `this`.
- BUT, they dont use prototype which may affect perfomance if you are using thousands of objects. So use normal constructors if you have thousands of object(like a physics engine).
- eg:
`function createUser(name) {`
`  const discordName = "@" + name;`
`  return { name, discordName };`
`}`

# Private variables and function.
- eg:
`- function objs(name){`
`    let res=0;`
`    const reso=()=>{return res};`
`    const reso1=()=>{res++; return res;}`
`    return {name, reso, reso1};`
`}`
`const oj=objs('daksh');`
`console.log(oj.name);`
`console.log(oj.reso());`
`console.log(oj.reso1());`
- in this we cannot return a private variable(here res) to object/s, to return it to object we have to return it through a function defined in factory function.
- This ensures encapsulation through factory function/closures.

# Prototypal inheritance with factories
-
`/**`
` * FACTORY FUNCTION: createUser (The "Base" Factory)`
` * Purpose: Creates a basic user with private reputation data.`
` */`
`function createUser(name) {`
`  const discordName = "@" + name;`
` `
`  // PRIVATE VARIABLE: Locked in this closure. `
`  // Global scope cannot see or change this directly.`
`  let reputation = 0;`
` `
`  // INTERFACE (Getters/Setters): The only way to interact with 'reputation'`
`  const getReputation = () => reputation;`
`  const giveReputation = () => { reputation++; };`
` `
`  return { name, discordName, getReputation, giveReputation };`
`}`
` `
`/**`
` * SUPER FACTORY: createPlayer (The "Derived" Factory)`
` * Pattern: Composition via Object.assign`
` */`
`function createPlayer(name, level) {`
`  // DATA FLOW: Passing 'name' down to the base factory to build the foundation.`
`  const user = createUser(name);`
` `
`  // PRIVATE VARIABLE: 'level' is scoped only to this function.`
`  const increaseLevel = () => { level++; };`
` `
`  // COMPOSITION: Merges a blank object {}, the 'user' object, and new functions.`
`  // NOTE: { increaseLevel } is shorthand for { increaseLevel: increaseLevel }`
`  return Object.assign({}, user, { increaseLevel });`
`}`
` `
`// --- EXECUTION ---`
` `
`let nameInput = prompt("Enter your name: ");`
`const obj1 = createUser(nameInput);`
` `
`let ch = prompt("Create a player? press y or n: ");`
` `
`if (ch === 'y') {`
`    // We pass 'nameInput' to ensure the Player has the correct name foundation.`
`    const P1 = createPlayer(nameInput, 0);`
` `
`    // DEBUGGING NOTES:`
`    console.log(P1.name);          // Output: "Daksh" (Inherited from user)`
`    console.log(P1.level);         // Output: undefined `
`    /* WHY UNDEFINED? `
`       'level' was never added to the return object in Object.assign. `
`       It exists in memory (Closure), but we lack a 'getLevel' function to see it.`
`    */`
` `
`    P1.increaseLevel();            // Increments internal 'level' to 1`
`} `
`else {`
`    console.log("Player creation skipped.");`
`}`

## Object.assign();
- it copies all properties from source onto the target
- Syntax: Object.assign(target,source1,source2....).
  
# The Module Pattern(Using IIFEs)
- NOTE: IIFE IS NOT A CONSTRUCTOR SO DON'T USE IT WITH OBJECTS, IIFE IS A FUNCTION!!!.
- IIFEs or Immediately Invoked Function Expression
- It is a JS function that runs as soon as it is defined.
- Used to create a private scope so they don't pollute the global scope.
- so IIFE are essentialty used to create a library/collection of private variables/function, and only way to access/get them is for the particular IIFE to return that particular variable/function.
- Syntax: `const func=(function () {// Logic goes here})();`
- eg:
  `const mods= (function(){`
`    let priv=0;`
`    const addpriv=()=>{priv++;};`
`    const getpriv=()=>priv;`
`    addpriv();`
`    return {getpriv};`
`})();`
`console.log(mods.getpriv());`