# npm
- npm is a gigantic repositories of libraries, plugin and other tools
- It provides us command-line-tool which we can use to install such tools.
- We will then have all our installed packages’ code locally, which we can import into our own files. 
  
# package.json
- npm revolves around package.json
- it’s a JSON file containing information about our project, such as its name or any dependencies and their version numbers. 
- npm can read this file and do things such as install all of the listed dependencies with the correct versions.    
- JSON (which stands for JavaScript Object Notation) is a lightweight, text-based format used for storing and exchanging data.
- It's basically like an id-card that contains metadata about our project
- so when we install/download a package from npm, package.json logs that package under "dependencies" section.
- The actual heavy code are downloaded into a folder named "node_modules".