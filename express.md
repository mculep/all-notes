# Dotenv

```javascript
npm i dotenv
```

-   Create a `.env` file (NO SPACES)

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

```
require('dotenv').config()

module.exports = {

  development: {
		username: process.env.DB_USER,
		password: process.env.DB_PASSWORD,
		database: process.env.DB_NAME,
 		host: process.env.DB_HOST,
		dialect: 'mysql'

  },

  test: {
		username: process.env.DB_USER,
		password: process.env.DB_PASSWORD,
		database: process.env.DB_NAME,
		host: process.env.DB_HOST,
		dialect: 'mysql'

  },

  production: {
		username: process.env.DB_USER,
		password: process.env.DB_PASSWORD,
		database: process.env.DB_NAME,
		host: process.env.DB_HOST,
		dialect: 'mysql'

  }

}
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

# Sequelize

-   Sequelize is a JS library that speaks to Postgres

app.use(express.urlencoded({ extended: true }));

# Sessions

-   Add sessions to the .gitignore file

Install the "session-file-store" and "express-session" modules

```javascript
npm i session-file-store express-session
```

-   ###### Import and configure the session middleware in "index.js"

```javascript
const session = require("express-session");

const FileStore = require("session-file-store")(session);

app.use(
    session({
        store: new FileStore(), // no options for now
        secret: process.env.SESSION_SECRET,
        saveUninitialized: false,
        resave: true,
        rolling: true,
        //maxAge: 1000 * 60 * 60 * 24 * 7,
        cookie: {
            maxAge: 1000 * 60 * 60 * 24 * 7,
        },
    })
);
```

-   ###### Make sure to add a `SESSION_SECRET` random string to your `.env` (and a placeholder in your `dist.env`)

-   Tell `nodemon` to ignore the `sessions` folder:

```javascript
"nodemonConfig": {
	"ignore": [
		"sessions/*"
	]
}
```

# New App

```javascript
npm init -y
npm i --save-dev nodemon
sequelize -cli (if you need it)
npm i express morgan express-es6-template-engine
touch index.js
echo "node modules" >> .gitignore
touch README.md
```

-   #### Insert in package.json

```javascript
"dev": "nodemon index.js",
```

-   #### In your index.js file

```javascript
const http = require(http);
const express = require(express);
const app = express ();
const server = http.createServer(app):

const homeRouter = require('./routers/home') <---(Do this after making your routers and home.js)

port = 3000;
host = "0.0.0.0";

app.use("/", homeRouter);
(Above app.use replaces below)
//app.get("/", (req, res)=>{
//  res.send(`<h1>Hello World!</h1>`)
//})

server.listen(port, host, () => {
	console.log("Running on port 3000");
});
```

-   #### <u>Run nodemon and check to see if app.get is working</u>

<img src="https://github.com/mculep/all-notes/blob/main/assets/Screen%20Shot%202020-12-19%20at%201.44.25%20AM.png" width="800px">

-   ###### Make a routers directory

> In that directory create a

```javascript
home.js;
```

###### In the `home.js`bring in the following

```javascript
const express = require(express);
const router = express.Router();

router.get("/", (req, res) => {
    res.send(`<h1>Hello from homeRouter`);
});
module.exports = router;
```

-   ###### Add this to your main `index.js`

```javascript
const homeRouter = require('./routers/home') <---(Do this after making your routers and home.js)
```

-   Also add this to your `index.js`.

```
app.use("/", homeRouter);
```

**Above will replace your**

_app.get("/", (req, res) => {_
\*\*

​ _res.send(`<h1>Hello World!</h1>`)_
_})_

in you main `index.js_ `

-   ##### It should look like this:

<img src="https://github.com/mculep/all-notes/blob/main/assets/router.get.png" width="800px">
