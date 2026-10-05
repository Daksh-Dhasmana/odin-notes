# How to install Node.js
- REMEMBER, WE WRITE NODE.JS IN PURE .JS NOT .JSX
- Install node.js from site and then run `npm init`, this will create a `package.json` file.
- Inside that `package.json` add this line too.
- 
```
{
  // ...
  "scripts": {

    "start": "node index.js",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  // ...
}
```