# Bundling
- In bundling, we provide the bundler with an entry point and then it builds an dependency graph from that file, combines necessary files and then gives an file as output which includes all necessary codes.
- A Dependency Graph is a visual map that shows how all files are connected, and to see these dependency graph, we have to use a developer tool or a plugin.
- It could do other things too, like Tree-Shaking(Removal of dead codes).
  
# WebPack
- In a webpack project, JS is boss of everything.
- It is a bundler for modern day JS application.
- You feed it a messy closet of hundreds of disorganized files (JavaScript, CSS, images, HTML), and it processes them all to output just a few highly optimized, neatly packed files that a web browser can understand instantly.
- Webpack merges hundreds of scattered code files into a single, optimized file so the browser doesn't have to waste time loading them one by one.
- To run webpack we use the command `npx webpack`.
- Before installing webpack create a package.json file with command: `npm init -y --init-type=module`, this creates a package.json file that is pre-configured to use modern JS syntax.
- After the above step, install the Webpack using `npm install --save-dev webpack webpack-cli` command.

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
- We can reuse this code for other projects too!!!
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

# Handling HTML
- We use the command `HtmlWebpackPlugin`.
- We run the following command `npm install --save-dev html-webpack-plugin`.
- Instead of maintaining an HTML file in dist folder, we create a source template(like ./src/template.html).
- When we run Webpack, the plugin takes over and does these 3 things:
   - Generates a fresh HTML file inside dist folder.
   - Copies over everything from source template(div tags, layout etc.).
   - Automatically injects the `<script>` tag for your bundle before `</body>` tag.
- `plugins: [`
    `new HtmlWebpackPlugin({`
      `template: "./src/template.html",`
    `}),`
- Make the file `template.html` inside src folder.
- After running the command `npx webpack`, there are now two files in dist: main.js and index.html.
- This piece of code is also reusable and installs HtmlWebpackPlugin.

# Loading CSS
- Run the following command : `npm install --save-dev style-loader css-loader`.
- In above command 
   - css-loader will read any CSS files we import in the JS file and store result in a string.
   - style-loader then takes that string(from css-loader) and adds the JS code that will apply styles to that page.
 - then we write:
    `module: {`
    `rules: [`
      `{`
        `test: /\.css$/i,`
        `use: ["style-loader", "css-loader"],`
      `},`
    `],`
  `},`
- All the above code does it's that, it tells Webpack that if it encounters a file ending with .css , it should use the listed loaders to process that CSS file/s.
  
# Loading Images
- For this, we can simply include them in CSS files using url().
- like this
`.hero-section {`
  `background-image: url('./assets/banner.jpg'); /* Relative path to your image */`
`}`
## Using HTML
- `// webpack.config.js`
`{`
  test: /\.html$/i,
  `use: ["html-loader"],`
`}`
- Write the following code inside webpack.config.js, and install `npm --save-dev html-loader`.

# WebPack Dev Server
- It's like the VS Code's Live Preview Extension, where it automatically refreshes whenever you saved changes.
- `webpack-dev-sever` is very similiar, meaning we dont have to run `npx webpack`, everytime we make changes.
- It works by bundling your code, every time you save a file that is used in bundle.
- We also use "source map", so that any/every error references files/lines and not the jumbled mess inside the single bundled .js file.
- we have to run the following command: `npx webpack serve`
- NOTE: Note that the webpack-dev-server only reads your webpack configuration when you start it. If you change the webpack config file while the dev server is running, it will not reflect those config changes. Use Ctrl + C in the terminal to kill it then rerun npx webpack serve to apply the new config.
  
`// webpack.config.js`
`import path from "node:path";`
`import HtmlWebpackPlugin from "html-webpack-plugin";`

`export default {`
  `mode: "development",`
  `entry: "./src/index.js",`
  `output: {`
    `filename: "main.js",`
    `path: path.resolve(import.meta.dirname, "dist"),`
    `clean: true,`
  `},`
  `devtool: "eval-source-map",`
  `devServer: {`
    `watchFiles: ["./src/template.html"],`
  `},`
  `plugins: [`
    `new HtmlWebpackPlugin({`
      `template: "./src/template.html",`
    `}),`
  `],`
  `"scripts": {`
    `"build": "webpack",`
    `"dev": "webpack serve",`
    `"deploy": "git subtree push --prefix dist origin gh-pages"`
  `},`
  `module: {`
    `rules: [`
      `{`
        `test: /\.css$/i`,
        `use: ["style-loader", "css-loader"],`
      `},`
      `{`
        `test: /\.html$/i,`
        `use: ["html-loader"],`
      `},`
      `{`
        `test: /\.(png|svg|jpg|jpeg|gif)$/i,`
        `type: "asset/resource",`
     ` },`
    `],`
  `},`
`};`

# Important commands install first
- `npx webpack`
- `npm init -y --init-type=module`
- `npm install --save-dev webpack webpack-cli`
- `npm install --save-dev html-webpack-plugin`
- `npm install --save-dev html-loader`
- `npm install --save-dev style-loader css-loader`
- `npx webpack serve`

# Important Github Commands for Webpack
- `git subtree push --prefix dist origin gh-pages`
- It solves a specific problem: how to deploy a website when your finished code is buried inside a subfolder (dist), but GitHub Pages expects it to be at the very top level.
- Like the `.html` file, which github expects to be at very top, but it's buried inside the dist folder.
- `git subtree push`: This tells Git, "Hey, I don't want to push this entire project. I only want to push a specific sub-folder (a 'subtree') as if it were its own standalone project."
- `--prefix dist`: This specifies exactly which folder to isolate. You are telling Git that the dist folder is the root folder for this push.
- `origin`: This is the shorthand name for your remote repository hosted on GitHub.
- `gh-pages`: This is the destination branch on GitHub where you want to send these files. 
- Suppose this is your Project Repo
- my-project/ (Your Main Repository)
├── src/
├── node_modules/
├── package.json
└── dist/                  <-- Only this folder contains your website
    ├── index.html
    └── bundle.js
- When we run github subtree push, it essentially ignores everything except dist, then it takes that dist and make a seperate "gh-pages" branch, it in which dist folder is on top, Like this.
- gh-pages branch (On GitHub)
├── index.html             <-- Now sitting perfectly at the top level!
└── bundle.js

- `"scripts": {`
  `"build": "webpack",`
  `"dev": "webpack serve",`
  `"deploy": "git checkout gh-pages && git merge main --no-edit && npm run build && git add dist -f && git commit -m 'Deployment commit' && git subtree`
   `push --prefix dist origin gh-pages && git checkout main"`
`}`
- This above, this thing is like one-for-all, everything related to webpack and shi.. and put it inside package.json() and delete the script inside webpack.config.js
- But ofc you have to write these too.
- `git branch gh-pages` this creates a seperate branch, gh-pages
- `npm run deploy`


## Advantages

* **Optimized Performance:** Uses features like **tree shaking** (removing unused code) and **code splitting** (loading code only when needed) to make websites load faster.
* **Handles Any File Type:** Through loaders, you can import CSS, images, and fonts directly into your JavaScript files, keeping related code organized together.
* **Great Developer Experience:** Its development server features **Hot Module Replacement (HMR)**, which updates your code in the browser instantly without refreshing the page.
* **Highly Customizable:** Offers a massive ecosystem of plugins that allow you to automate almost any build task, from minifying code to managing environment variables.

## Disadvantages

* **Steep Learning Curve:** Configuring `webpack.config.js` from scratch is notoriously complex and overwhelming for beginners (often called "configuration hell").
* **Slower Build Times:** Because it is built on older Node.js architecture, processing very large codebases can feel sluggish compared to newer tools.
* **Overkill for Small Projects:** Setting up a complex bundler adds unnecessary boilerplate and frustration if you are just building a simple, few-page website.


- NOTE: After adding gitignore, add these two folders as well: node_modules`node_modules/` and dist`dist/` 