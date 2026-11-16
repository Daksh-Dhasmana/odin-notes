# MongoDB
- It is a popular NoSQL database designed to store data in flexible, JSON-like documents rather than traditional rows and tables.
- It is a document database not RDBMS.
- Document DB are usually classified under NOSQL umbrella term
## Advantages:
- ### 1) Flexibility ###
    - Documents in the same collection don't need to have the exact exact same fields. If one user has a phone number and another doesn't, MongoDB doesn't care; it won't crash or throw a schema error.
- ### 2) JS Friendly ###
    - Since MongoDB stores data in JSON-like format(called BSON), it feels natural to work alongside Node, react etc.
- ### 3) Easy Scaling ###
    - It is built to handle massive amounts of data and can scale across multiple servers easily.

# Documents
- It is the basic unit of MongoDB
- A JSON-like record within a collection(like a row).

# Collection
- A container for documents(like table).

# Field
- A key-value pair within a document(like a column).

# SQL vs NoSQL
- Scalability
  - NoSQL: Designed to scale horizontally by adding more servers, distributing load across multiple nodes.
  - SQL: Typically scales vertically by adding more resources to a single server, which has limits and can be costly. Horizontal scaling(Sharding) can be complex and less efficient.
- Schema Flexibility
  - NoSQL: Schema-less design allows for easy storage of diverse and rapidly changing data without needing to alter the schema 
  - SQL: Requires a pre-defined. Altering schema(eg: adding new columns) can be complex and time-consuming with large datasets
- Perfomance
  - NoSQL: Optimized for high speed read and write operations, making it ideal for real time analysis and data processing.
  - SQL: Though performant, can suffer from slower read/write operation when dealing with very large datasets due to ACID transaction overhead and complex joins.
- Handling Unstructered Data
  - NoSQL: Efficiently handles unstructured or semi-structured data which is common in real-time analytics.
  - SQL: Best suited for structured data, Handling unstructed data requires complex transformations or additional systems(eg: strong JSON data in columns).