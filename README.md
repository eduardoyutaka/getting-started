# Welcome to the Yutaka Developer Bootcamp

## Getting Started

1. Install Git
2. Make a GitHub Account
3. Install Atom Editor / Sublime Text / Visual Studio Code
4. Install Node.js
5. Install Yarn
6. Install GraphQL.js
  - Getting Started With GraphQL.js
  - Running an Express GraphQL Server

## Install Git

- [https://git-scm.com/download/win](https://git-scm.com/download/win)

#### Select Components

- [ ] Additional icons
  - [ ] On the Desktop
- [x] Windows Explorer integration
  - [x] Git Bash Here
  - [x] Git GUI Here
- [x] Git LFS (Large File Support)
- [x] Associate .git\* configuration files with the default text editor
- [x] Associate .sh files to be run with Bash
- [ ] Use a TrueType font in all console windows
- [ ] Check daily for Git Windows updates

#### Choosing the default editor used by Git

> Use Vim (the ubiquitous text editor) as Git's default editor

#### Adjusting your PATH envitonment

> Git from the command line and also from 3rd-party software

#### Choosing HTTPS transport backend

> Use the OpenSSL library

#### Configuring the line ending conversations

> Checkout Windows-style, commit Unix-style line endings

#### Configuring the terminal emulator to use with Git Bash

> Use MinTTY (the default terminal of MSYS2)

#### Configuring extra options

- [x] Enable file system caching
- [x] Enable Git Credential Manager
- [ ] Enable symbolic links

#### Configuring experimental options

- [ ] Enable experimental, built-in add -i/-p

#### Replacing in-use files

> Install

## Make a GitHub Account

- [https://github.com](https://github.com)

## Install Atom Editor / Sublime Text / Visual Studio Code

- [https://atom.io/](https://atom.io/)
- [https://www.sublimetext.com/](https://www.sublimetext.com/)
- [https://code.visualstudio.com/](https://code.visualstudio.com/)

## Install Node.js

- [https://nodejs.org/en/](https://nodejs.org/en/) (10.16.0 LTS)

## Install Yarn

- [https://yarnpkg.com/lang/en/docs/install/](https://yarnpkg.com/lang/en/docs/install/) (Stable 1.16.0)

## Install GraphQL.js

- [https://github.com/graphql/graphql-js](https://github.com/graphql/graphql-js)

> `$ cd ~`
> `$ mkdir Developer`
> `$ cd Developer/`
> `$ mkdir graphql`
> `$ cd graphql/`
> `$ yarn add graphql`

## Getting Started With GraphQL.js

- [https://graphql.org/graphql-js/](https://graphql.org/graphql-js/)

> `$ mkdir src`
> `$ cd src/`
> `$ vim server.js`

**server.js**
```
var { graphql, buildSchema } = require('graphql');

// Construct a schema, using GraphQL schema language
var schema = buildSchema(`
  type Query {
    hello: String
  }
`);

// The root provides a resolver function for each API endpoint
var root = {
  hello: () => {
    return 'Hello world!';
  },
};

// Run the GraphQL query '{ hello }' and print out the response
graphql(schema, '{ hello }', root).then((response) => {
  console.log(response);
});
```

## Running an Express GraphQL Server

- [https://graphql.org/graphql-js/running-an-express-graphql-server/](https://graphql.org/graphql-js/running-an-express-graphql-server/)

> `$ npm install express express-graphql graphql --save`

```
var express = require('express');
var graphqlHTTP = require('express-graphql');
var { buildSchema } = require('graphql');

// Construct a schema, using GraphQL schema language
var schema = buildSchema(`
  type Query {
    hello: String
  }
`);

// The root provides a resolver function for each API endpoint
var root = {
  hello: () => {
    return 'Hello world!';
  },
};

var app = express();
app.use('/graphql', graphqlHTTP({
  schema: schema,
  rootValue: root,
  graphiql: true,
}));
app.listen(4000);
console.log('Running a GraphQL API server at localhost:4000/graphql');
```
