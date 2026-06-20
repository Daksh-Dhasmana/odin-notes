# Bundling
- In bundling, we provide the bundler with an entry point and then it builds an dependency graph from that file, combines necessary files and then gives an file as output which includes all necessary codes.
- A Dependency Graph is a visual map that shows how all files are connected, and we can see these dependency graph, we have to use a developer tool or a plugin.
- It could do other things too, like Tree-Shaking(Removal of dead codes).
  
# WebPack
- It is a bundler for modern day JS application.
- You feed it a messy closet of hundreds of disorganized files (JavaScript, CSS, images, HTML), and it processes them all to output just a few highly optimized, neatly packed files that a web browser can understand instantly.
- Webpack merges hundreds of scattered code files into a single, optimized file so the browser doesn't have to waste time loading them one by one.

# Src and Dist
- When dealing with Webpack or other bundlers, we have two important directories: src(source) and dist(distribution).
- src is where we keep our source code.
- When we run Webpack to bundle our code, it will output the bundled code into "dist" directory.
- If someone forks or clones our repo, then they would not need the dist directory, they would bundle their source code into their own dist directory.
- To deploy our website, we would need only the dist code and nothing else!.
- NOTE: Work inside src, build into dist and then deploy it from here.

# Bundling JavaScript
- We created two files inside the src directory and then we created a `webpack.config.js` file which contains necessary details for bundling like entry point, output destination etc.
- then we run the webpack using command `npx webpack`.
- Then webpack creates a dist directory with main.js file an when we run this file, we can the outputs

# Webpack code structure
`// webpack.config.js`
`import path from "node:path";`
``
`export default {`
`  mode: "development",`
`  entry: "./src/index.js",`
`  output: {`
`    filename: "main.js",`
`    path: path.resolve(import.meta.dirname, "dist"),`
`    clean: true,`
`  },`
`};`

- entry: A file path from the config file to whichever file is our entry point, which in this case is src/index.js.
- output: An object containing information about output bundle.
   - filename: name of output file, we can change it
   - path: the path to output directory, in this case dist.
   - clean: If we include this option and set it to true, then each time we run Webpack to bundle, it will empty the output directory first before bundling the files into it. This helps us keep dist clean, so it only contains the files produced by the most recent bundling.