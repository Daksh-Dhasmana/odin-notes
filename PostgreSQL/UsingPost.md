# Using PostgreSQL with express
-  
```
const { Pool } = require("pg");

// All of the following properties should be read from environment variables
// We're hardcoding them here for simplicity
module.exports = new Pool({
  host: "localhost", // or wherever the db is hosted
  user: "<role_name>",
  database: "top_users",
  password: "<role_password>",
  port: 5432 // The default port
});
```
- In above code, we are connecting our database with express to use it.
-  
```
const pool = require("./pool");

async function getAllUsernames() {
  const { rows } = await pool.query("SELECT * FROM usernames");
  return rows;
}

async function insertUsername(username) {
  await pool.query("INSERT INTO usernames (username) VALUES ($1)", [username]);
}

module.exports = {
  getAllUsernames,
  insertUsername
};
```
- Now in above code, we are defining SQL queries and making a function to use these said queries
- Here. Pool is a connection pool class exported by the `pg (node-postgres)` package. Instead of opening and closing a brand-new TCP connection to PostgreSQL every single time your Express server handles a request, Pool maintains a reusable group of open connections and hands them out on demand.
- In above code, why did we use $1 instead of `${username}`? there are 4 main reason:
  - 1) $1 is a placeholder of sorts
  - 2) pg/postgre knows that $1 can be substituted
  - 3) whatever we write into $1 is treated as a literal value
  - 4) since $1 is not a SQL query/command, attacker can't use SQL injection