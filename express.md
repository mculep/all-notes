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

# MVC (Models, Views, and Controllers)

> Express.js uses MVC concept

-   Model - Interacts with the database and commmunicates with controllers. Represents data in your code and you are able to work with the data ex: save, fetch, to and from a file.

-   View - Is what you see on screen. Rendering HTML contents and communicates with controller & model. Uses template engines like es6renderer.

-   Controller - is the connection point between the models and views. Takes in user input (GET, POST etc), controller gets data from the model and passes data to the view and the template engine takes over.

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
//Main index.js
const http = require(http);
const express = require(express);
const app = express ();
const server = http.createServer(app):
const es6Renderer =require("express-es6-template-engine")

app.engine('html', es6Renderer);
app.set('views', 'templates');
app.set('view engine', 'html');


port = 3000;
host = "0.0.0.0";


app.get("/", (req, res)=>{
  res.send(`<h1>Hello World!</h1>`)
})

server.listen(port, host, () => {
	console.log("Running on port 3000");
});
```

-   #### <u>Run nodemon and check to see if app.get is working</u>

<img src="https://github.com/mculep/all-notes/blob/main/assets/Screen%20Shot%202020-12-19%20at%201.44.25%20AM.png" width="800px">

-   ###### Make a routers directory

> In that directory create a `home.js`

###### In the routers `home.js` bring in the following

```javascript
//Routers home.js
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

-   ###### Also add this to your main `index.js`.

```
app.use("/", home);
```

**Above will replace your**

_app.get("/", (req, res) => {_
\*\*

​ _res.send(`<h1>Hello World!</h1>`)_
_})_

in your main `index.js`

-   ### It should look like this:

<img src="https://github.com/mculep/all-notes/blob/main/assets/router.get.png" width="800px">

-   ###### In your main `index.js` add in morgan

> Morgan is a middleware for `node.js` it logs incoming traffic and requests

```javascript
const morgan = require("morgan");
const logger = morgan("tiny");

app.use(logger);
```

> Here is the pancake stack:

<img src="https://github.com/mculep/all-notes/blob/main/assets/pancake-stack-middleware-to-router.png" width="800px">

> Check to see if everything shows up in the browser

-   Create a **controllers** directory above routers directory
-   Inside controllers, create a `home.js` file

```javascript
// Controllers home.js
const home = (req, res) => {
    res.send(`<h1>Hello from homeController</h1>`);
};

module.exports = {
    home,
};
```

-   Go to your **router** `home.js` file & modify

```javascript
router.get("/", (req, res) => {
    res.send(`<h1>Hello from homeRouter</h1>`);
});
```

_TO THE CODE BELOW_

```javascript
router.get("/", home);
```

**_router.get("/", home); calls the home function in controllers and sends to the browser_**

-   Also add the following below in the **router** `home.js`

> You need to deconstruct the "home" to avoid getting undefined.

```javascript
const { home } = require("../controllers/home");
```

> A Visual of how everything is working:

<img src="https://github.com/mculep/all-notes/blob/main/assets/controllers.png" width="800px">

-   ###### Now create a `templates` directory

-   ###### Inside that directory create a file called `home.html`

```html
<h1>Hello World from template</h1>
```

-   ###### Go back to your **controllers** `home.js` and include this:

```javascript
res.render("home");
```

**And delete**

```
res.send(`<h1>Hello from homeController</h1>`);
```

<img src="https://github.com/mculep/all-notes/blob/main/assets/templates.png" width="800px">

### Movies object: an array of 3 movie titles

> Working with a .json file and using this data in the template

-   ###### Create a `data.json`

```javascript
[
    {
        id: 1,
        title: "Nacho Libre",
    },
    {
        id: 2,
        title: "School Of Rock",
    },
    {
        id: 3,
        title: "North Shore",
    },
];
```

-   ###### In your main `index. js` require the `data.json` file.

```javascript
const data = require("./data.json");
```

> _you can view it by console.log(data); to see if data shows in terminal_

-   ###### Create a route in your main `index.js`

> By doing this, `res.send(data);` will send this to your browser

```javascript
app.get("/movies", (req, res) = > {
  res.send(data);
});
```

-   ###### in your templates directory create a `moviesList.html`

```html
<h1>Hello from moviesList.html</h1>
```

-   ###### Still in your main `index. js` , replace res.send(data); with:

> res.render will read the text from movies.html and send it to the browser

```javascript
res.render("movieList");
```

<img src="https://github.com/mculep/all-notes/blob/main/assets/templates2.png" width="800px">

-   ###### Adding a locals object

> Locals adds variables and values to the template
>
> The "movies variable" needs to be mapped in the `movieList.html ` to show the value "data"

```javascript
app.get("/movies", (req, res) => {
    res.render("moviesList", {
        locals: {
            movies: data,
        },
    });
});
```

<img src="https://github.com/mculep/all-notes/blob/main/assets/locals.png" width="800px">

-   Using that local "movies" variable in your` movieList.html`

> `.map` converts the array of objects into an array of HTML strings.

```html
<h2>
    ${ movies.map(d => `
    <p>${d.title}</p>
    `).join(''); }
</h2>
```

<img src="https://github.com/mculep/all-notes/blob/main/assets/map.png" width="800px">
