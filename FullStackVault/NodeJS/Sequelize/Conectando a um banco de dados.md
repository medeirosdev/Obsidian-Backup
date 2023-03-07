To connect to the database, you must create a Sequelize instance. This can be done by either passing the connection parameters separately to the Sequelize constructor or by passing a single connection URI:

const { Sequelize } = require('sequelize');

// Option 1: Passing a connection URI
const sequelize = new Sequelize('sqlite::memory:') // Example for sqlite
const sequelize = new Sequelize('postgres://user:pass@example.com:5432/dbname') // Example for postgres

// Option 2: Passing parameters separately (sqlite)
const sequelize = new Sequelize({
  dialect: 'sqlite',
  storage: 'path/to/database.sqlite'
});

// Option 3: Passing parameters separately (other dialects)
const sequelize = new Sequelize('database', 'username', 'password', {
  host: 'localhost',
  dialect: /* one of 'mysql' | 'postgres' | 'sqlite' | 'mariadb' | 'mssql' | 'db2' | 'snowflake' | 'oracle' */
});

The Sequelize constructor accepts a lot of options. They are documented in the [API Reference](https://sequelize.org/api/v6/class/src/sequelize.js~Sequelize.html#instance-constructor-constructor).

### Testing the connection[​](https://sequelize.org/docs/v6/getting-started/#testing-the-connection "Direct link to heading")

You can use the `.authenticate()` function to test if the connection is OK:

try {
  await sequelize.authenticate();
  console.log('Connection has been established successfully.');
} catch (error) {
  console.error('Unable to connect to the database:', error);
}

### Closing the connection[​](https://sequelize.org/docs/v6/getting-started/#closing-the-connection "Direct link to heading")

Sequelize will keep the connection open by default, and use the same connection for all queries. If you need to close the connection, call `sequelize.close()` (which is asynchronous and returns a Promise).

NOTE

Once `sequelize.close()` has been called, it's impossible to open a new connection. You will need to create a new Sequelize instance to access your database again.


## Terminology convention[​](https://sequelize.org/docs/v6/getting-started/#terminology-convention "Direct link to heading")

Observe that, in the examples above, `Sequelize` refers to the library itself while `sequelize` refers to an instance of Sequelize, which represents a connection to one database. This is the recommended convention and it will be followed throughout the documentation.

## Tip for reading the docs[​](https://sequelize.org/docs/v6/getting-started/#tip-for-reading-the-docs "Direct link to heading")

You are encouraged to run code examples locally while reading the Sequelize docs. This will help you learn faster. The easiest way to do this is using the SQLite dialect:
const { Sequelize, Op, Model, DataTypes } = require("sequelize");
const sequelize = new Sequelize("sqlite::memory:");

// Code here! It works!
