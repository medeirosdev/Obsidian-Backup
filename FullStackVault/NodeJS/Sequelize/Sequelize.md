[[Sequelize]]
Basicamente Faz operações SQL dentro do seu Script NodeJS

Sequelize is an easy-to-use and promise-based [Node.js](https://nodejs.org/en/about/) [ORM tool](https://en.wikipedia.org/wiki/Object-relational_mapping) for [Postgres](https://en.wikipedia.org/wiki/PostgreSQL), [MySQL](https://en.wikipedia.org/wiki/MySQL), [MariaDB](https://en.wikipedia.org/wiki/MariaDB), [SQLite](https://en.wikipedia.org/wiki/SQLite), [DB2](https://en.wikipedia.org/wiki/IBM_Db2_Family), [Microsoft SQL Server](https://en.wikipedia.org/wiki/Microsoft_SQL_Server), and [Snowflake](https://www.snowflake.com/). It features solid transaction support, relations, eager and lazy loading, read replication and more.

## Installing[​](https://sequelize.org/docs/v6/getting-started/#installing "Direct link to heading")

Sequelize is available via [npm](https://www.npmjs.com/package/sequelize) (or [yarn](https://yarnpkg.com/package/sequelize)).

```
npm install --save sequelize
```

You'll also have to manually install the driver for your database of choice:

```
# One of the following:$ npm install --save pg pg-hstore # Postgres$ npm install --save mysql2$ npm install --save mariadb$ npm install --save sqlite3$ npm install --save tedious # Microsoft SQL Server$ npm install --save oracledb # Oracle Database
```

Veja [[Conectando a um banco de dados]]
