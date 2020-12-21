# Dontenv

```javascript
npm i dotenv
```

-   Create a `.env` file (NO SPACES)

> Make sure that .env is in your .gitignore

```
DB_USER=paste_from_elephantsql
DB_PASSWORD=paste_from_elephantsql
DB_NAME=paste_from_elephantsql
DB_HOST=paste_from_elephantsql
```

-   Create a `.sequelizerc`

```javascript
const path = require("path");

module.exports = {
    config: path.resolve("server/config", "config.js"),
    "models-path": path.resolve("server", "models"),
    "seeders-path": path.resolve("server", "seeders"),
    "migrations-path": path.resolve("server", "migrations"),
};
```

Create a `server/config/config.js`

```javascript
require("dotenv").config();

module.exports = {
    development: {
        username: process.env.DB_USER,
        password: process.env.DB_PASSWORD,
        database: process.env.DB_NAME,
        host: process.env.DB_HOST,
        dialect: "mysql",
    },

    test: {
        username: process.env.DB_USER,
        password: process.env.DB_PASSWORD,
        database: process.env.DB_NAME,
        host: process.env.DB_HOST,
        dialect: "mysql",
    },

    production: {
        username: process.env.DB_USER,
        password: process.env.DB_PASSWORD,
        database: process.env.DB_NAME,
        host: process.env.DB_HOST,
        dialect: "mysql",
    },
};
```

-   Create a `.sequelizerc`

```javascript
const path = require("path");

module.exports = {
    config: path.resolve("server/config", "config.js"),
    "models-path": path.resolve("server", "models"),
    "seeders-path": path.resolve("server", "seeders"),
    "migrations-path": path.resolve("server", "migrations"),
};
```
