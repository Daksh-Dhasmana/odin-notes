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
- 