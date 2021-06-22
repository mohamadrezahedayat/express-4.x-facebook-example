This example demonstrates how to use [Express](https://expressjs.com) 4.x and
[Passport](https://www.passportjs.org) to log users in with [Facebook](https://www.facebook.com).
Use this example as a starting point for your own web applications.

## Quick Start

To get started with this example, clone the repository and install the
dependencies.

```bash
$ git clone git@github.com:passport/express-4.x-facebook-example.git
$ cd express-4.x-facebook-example
$ npm install
```

This example requires credentials from Facebook, which can be obtained by
[creating](https://developers.facebook.com/docs/development/create-an-app) an
app in the [App Dashboard](https://developers.facebook.com/apps).
The OAuth redirect URI of the app should be set to: `http://localhost:3000/oauth2/redirect/www.facebook.com`

Once credentials have been obtained, create a `.env` file and add the following
environment variables:

```
FACEBOOK_CLIENT_ID={{INSERT_APP_ID_HERE}}
FACEBOOK_CLIENT_SECRET={{INSERT_APP_SECRET_HERE}}
```

Start the server.

```bash
$ npm start
```

Navigate to [`http://localhost:3000`](http://localhost:3000).

## Overview

This example illustrates how to use [Passport](https://www.passportjs.org) and
the [`passport-facebook`](https://www.passportjs.org/packages/passport-facebook/)
strategy within an [Express](https://expressjs.com) application to log users in
with [Facebook](https://www.facebook.com).

The example builds upon the scaffolding created by [Express generator](https://expressjs.com/en/starter/generator.html),
and uses [EJS](https://ejs.co) as a view engine and plain CSS for styling.  This
scaffolding was generated by executing:

```
$ express --view ejs express-4.x-facebook-example
```

The example uses [SQLite](https://www.sqlite.org) for storing user accounts.
SQLite is a lightweight database that works well for development, including this
example.

Added to the scaffolding are files which add authentication to the application.

* [`boot/db.js`](boot/db.js)

  This file initializes the database by creating the tables used to store user
  accounts and credentials.

* [`boot/auth.js`](boot/auth.js)

  This file initializes Passport.  It configures the Facebook strategy and supplies
  the serialization functions used for session management. 

* [`routes/auth.js`](routes/auth.js)

  This file defines the routes used for authentication.  In particular, there are
  two routes used to authenticate with Google:
  
  - `GET /login/federated/www.facebook.com`
  
    This route begins the authentication sequence by redirecting the user to
    Facebook.
  
  - `POST /oauth2/redirect/www.facebook.com`
  
  This route completes the authentication sequence when Facebook redirects the
  user back to the application.  When a new user logs in, a user account is
  automatically created and their Facebook account is linked.  When an existing
  user returns, they are logged in to their linked account.

## License

[The Unlicense](https://opensource.org/licenses/unlicense)
