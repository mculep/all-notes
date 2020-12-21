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
