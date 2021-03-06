# nmess

[![travis-ci](http://img.shields.io/travis/edge/nmess-generator.svg?style=flat-square)](https://travis-ci.org/edge/nmess-generator)
[![npm version](https://img.shields.io/npm/v/nmess.svg?style=flat-square)](https://npmjs.org/package/nmess)
[![downloads](http://img.shields.io/npm/dm/nmess.svg?style=flat-square)](https://npmjs.org/package/nmess)
[![license](http://img.shields.io/npm/l/nmess.svg?style=flat-square)](http://opensource.org/licenses/MIT)

## In a Nutshell

```
What `nmess` does for you:
    lays out an Express Node.js server
    scaffolds server routing
    prepares a database connection
    sets up a gulpfile that:
        compiles ECMAScript 6 to 5
        uglifies Javascript
        compiles Stylus to CSS
        uglifies CSS
    includes client assets such as:
        jQuery
        Bootstrap
        Angular
        Socket.IO
    readies WebSockets
    sets up miscellaneous server objects
```

## About

`nmess` is a modern and developer-friendly skeleton application generator that implements the MESS stack: MongoDB, Express.js, Socket.IO, and Stylus, which uses Jade as the templating language. It is designed so that the developer can immediately start being productive, instead of writing boilerplate preparation code and build systems for every new project. `nmess` has been cleverly implemented to scale with future development. `nmess` now includes Bootstrap 3 by default and automatically extends the project into the MEAN stack, integrating Angular into the application.

The generator prepares various server utilities and components such as a configurable REST API, Socket.IO connection, database controllers, gulp build system, and HTTP response codes, and organizes source files in an extensible and logical manner.

The included gulp build system automatically optimizes and minifies client assets such as .styl sheets and Javascripts. Using a build system instead of middleware for client assets improves reliability and response time for all requests.

`nmess` is great for single page applications, hybrid sites, web services, and API endpoints.

**`nmess` now provides automatic local caching by SHA-comparison and source management, so a fully functional environment can be set up while offline, and generation while online is expedited as well.**

The actual skeleton code may be found at https://github.com/edge/nmess.

**`nmess` is being developed in discord with MEAN.IO. `nmess` quickly prepares all assets that you need to supplement and encourage your design ideas, while MEAN.IO takes a more restrictive CMS approach.**

`nmess` was inspired by and intends to replace `express-generator` and `node-boilerplate`, both projects with great initiatives but undermaintained.

## Table of Contents
* [Installation](#installation)
* [Generator](#generator)
    * [Help](#help)
    * [Usage](#usage)
    * [Visual](#visual)
* [Deployment](#deployment)
* [Dependencies](#dependencies)
* [Documentation](#documentation)
* [Todo](#todo)

## Installation
```sh
sudo npm install -g nmess
```

## Generator

### Help
```sh
nmess -h
```

```
  Usage: nmess <command> [options]


  Commands:

    new <application>  create new application
    dev                run application in development mode
    pro                run application in production mode
    make               compile application assets

  Options:

    -h, --help                   output usage information
    -V, --version                output the version number
    -d, --directory [directory]  Application directory [name]
    -s, --secret [secret]        Session secret [uuid.v4()]
    -b, --database [db]          Local database path ['localhost/' + name]
    -p, --port [port]            Server listening port [3000]
```

### Usage
```sh
nmess new myapp
```

```
Up-to-date skeleton found in cache.
Installing...
Populating...
Building...
Node MESS Application generated with:
name:      myapp
directory: myapp
secret:    cd1b725d-8c41-4d30-a736-105db3cf8a14
db:        localhost/myapp
port:      3000
```

```
myapp/
    bin/
        www
    client/
        css/
            error.styl
            myapp.styl
        js/
            index.js
            myappApp.js
    db/
        control.js
        init.js
        model.js
    public/
        css/
            bootstrap.css
            error.css
            myapp.css
        fonts/
            glyphicons-halflings-regular.eot
            glyphicons-halflings-regular.ttf
            glyphicons-halflings-regular.woff2
            glyphicons-halflings-regular.svg
            glyphicons-halflings-regular.woff
            OpenSans.ttf
        img/
            favicon.ico
        js/
            angular.js
            angular-animate.js
            angular-route.js
            angular.js
            bootstrap.js
            index.js
            jquery.js
            myappApp.js
            socket.io.js
        robots.txt
    routes/
        api.js
        index.js
    utils/
        httpres.json
    views/
        base.jade
        error.jade
        index.jade
    .gitignore
    app.js
    config.json
    gulpfile.js
    nodemon.json
    package.json
    README.md
    router.js
```

### Visual
[![install](http://i.j2.io/30OP.png)](http://i.j2.io/30OP.png)
[![initial](http://i.j2.io/FX1K.png)](http://i.j2.io/FX1K.png)

### Deployment
#### Production
```sh
cd ./myapp && nmess pro
```
#### Development
```sh
cd ./myapp && nmess dev
```

### Dependencies
#### Production
These production modules (`npm install --save`) are required to run the server.
```
body-parser
compression
express
express-session
jade
mongoose
morgan
socket.io
```
#### Development
These development modules (`npm install --save-dev`) are required to compile the templates and stylesheets.
```
gulp
gulp-babel
gulp-cached
gulp-stylus
gulp-uglify
```
#### Global
These global modules (`npm install -g`) are required to run the application in development mode.
```
gulp
nodemon
```
#### Machine
These technologies are required to run the server, but features using them disengage gracefully if missing.
```
mongodb
```

### Documentation
```
d - directory for
m - module for
```

```
__name__/                                       // d - all application files
    bin/                                        // d - executable scripts
        www                                     // server start script
    client/                                     // d - client assets
        css/                                    // d - stylesheets
            __name__.styl                       // main stylesheet
            error.styl                          // error page stylesheet
            index.styl                          // index page stylesheet
        js/                                     // d - client scripts
            __name__App.js                      // primary Angular application
            index.js                            // index page script
    db/                                         // d - database design
        control.js                              // m - database business logic
        init.js                                 // m - database connection
        model.js                                // m - database model definitions
    public/                                     // d - client-accessible resources
        css/                                    // d - files compiled from client/css/
            __name__.css                        // compiled from client/css/__name__.styl
            error.css                           // compiled from client/css/error.styl
            index.css                           // compiled from client/css/index.styl
        font/                                   // d - client fonts
            glyphicons-halflings-regular.eot    // Bootstrap Glyphicons font
            glyphicons-halflings-regular.ttf    // Bootstrap Glyphicons font
            glyphicons-halflings-regular.woff2  // Bootstrap Glyphicons font
            glyphicons-halflings-regular.svg    // Bootstrap Glyphicons font
            glyphicons-halflings-regular.woff   // Bootstrap Glyphicons font
            OpenSans.ttf                        // Open Sans font
        img/                                    // d - image assets
            favicon.ico                         // n.js tab icon
        js/                                     // d - client scripts
            __name__App.js                      // compiled from client/js/__name__App.js
            angular.js                          // Angular 1.3.14, minified
            angular-animate.js                  // Angular Animate, minified
            angular-route.js                    // Angular Route, minified
            bootstrap.js                        // Bootstrap 3.3.2, minified
            index.js                            // compiled from client/js/index.js
            jquery.js                           // jQuery 1.11.2, minified
            socket.io.js                        // Socket.IO 1.3.5, minified
        robots.txt                              // robots.txt
    routes/                                     // d - server routes
        api.js                                  // m - api route
        index.js                                // m - index route
    util/                                       // d - server utilities
        httpres.json                            // HTTP response code list
    views/                                      // d - page templates
        base.jade                               // base template
        error.jade                              // error page template
        index.jade                              // index page template
    .gitignore                                  // .gitignore
    app.js                                      // m - main application interface
    config.json                                 // application configuration
    gulpfile.js                                 // m - gulp build system
    nodemon.json                                // nodemon server configuration
    package.json                                // package configuration
    README.md                                   // application README
    router.js                                   // m - server route coordination
```

### Todo
- Dynamically add database models and controllers
- Deepen Angular integration
- Add sourcemaps to build system
