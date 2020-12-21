## simple-login

Shows how to use `bcryptjs` to store password hashes.

A hash is the result of running a plain text password (what you type) into an unreadable string of numbers and letters.

A hash can be recomputed by passing the original password to bcrypt, but it's mathematically impossible to turn a hash into the original password.

The `salt` is an additional input that bcrypt uses to randomize the hash. The salt itself is generated randomly. Bcrypt tacks this on to the end of the hash.

The purpose of a salt is not that it is secret - it is so that two passwords produce two different hashes.

## Install the `bcryptjs` node module

```sh
npm i bcryptjs
```

## Ensure username is unique

From https://sequelize.org/master/manual/validations-and-constraints.html

Edit the migration and make sure that the username must be unique in your database.
In addition, ensure that they must have a value (`allowNull: false`).

```js
      username: {
          type: Sequelize.STRING,
          allowNull: false,
          unique: true
      },
      hash: {
          type: Sequelize.STRING,
          allowNull: false
      },
```

## Generate a hash from the password

```js
const salt = bcrypt.genSaltSync(10);
const hash = bcrypt.hashSync(password, salt);
```

## Get the user by their username

```js
const user = await User.findOne({
    where: {
        username,
    },
});
```

## Ask bcrypt to check a password against a hash

```js
const isValid = bcrypt.compareSync(password, user.hash);
```
