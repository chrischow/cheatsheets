---
layout: default
title: Express Projects
nav_order: 2
parent: Backend Development
---

# Express Projects
{: .no_toc }

1. TOC
{:toc}

## `package.json`
This template is for an Express app built in TypeScript.

- Express
- Mongoose

```json
{
  "name": "project-name",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "build": "npx tsc",
    "start": "node dist/index.js",
    "dev": "concurrently \"npx tsc --watch\" \"nodemon -q dist/index.js\"",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "dotenv": "^16.0.3",
    "express": "^4.18.2",
    "mongoose": "^6.7.2"
  },
  "devDependencies": {
    "@types/express": "^4.17.14",
    "@types/node": "^18.11.9",
    "concurrently": "^7.5.0",
    "nodemon": "^2.0.20"
  }
}

```

## Folder Structure

```
.
├── index.ts / app.ts   # Main app 
├── db                  # Database functions: connect
├── controllers         # Functions used in routes
├── middleware          # Key functions for processing requests and returning responses
│   ├── begin-with-the-crazy-ideas. Textile
│   └── on-simplicity-in-technology. Markdown
├── models              # Object models
├── public
│   ├── index.html
│   └── styles.css
└── routes              # Routers for given URL prefixes
```

### Entrypoint
The main entry point for the app. Usually called `index.ts` or `app.ts`.

- Initialises the app
- Registers [middleware](#middleware) and places them in the right order (relative to each other and the routes)
- Registers the [routes](#routes)
- Connects to the database using the function(s) from [DB](#db)
- Starts the server after successful connection to the database

### DB
The `db` folder contains the function(s) to connect to the database(s). The function(s) is(are) exported, and called in the [entrypoint](#entrypoint).

### Controllers
Functions encapsulating the logic used for each route.

- Separate into several files - one per major entity
- Each function takes a `request` and `response` object as arguments, and returns a response (status + data/rendered template)
- Imports [object models](#models) for CRUD operations
- Exports controllers, which are called in [routes](#routes)

### Middleware
Middleware functions that receive a request, process data, and call the next function, which could be more middleware or a final piece of logic.

- Separate into several files - one per category of middleware
- Each middleware function takes `request`, `response` and `next` objects/functions as arguments, and either (1) calls `next()` or (2) returns a final response
- Exports middleware functions, which are called in the [entrypoint](#entrypoint)

### Models
Object models for all entities in separate files:

- Defines schemas, including any validators
- Defines models using respective schemas
- Exports the models, which are called in [controllers](#controllers)

### Public
WIP

### Routes
Imports associated controllers for logic at each endpoint.

- Defined by URI prefix (e.g. `/api/v1/people` is `/` and `api/v1/people/:id` is `:id`)
- Routes are defined in chains (e.g. `router.route('/').get(<controller 1>).post(<controller 2>`)
- Routes are uniquely defined by URI prefix and HTTP method
- Logic is taken from [controllers](#controllers)
- Exports routers, which are called in the [entrypoint](#entrypoint)

## Generic Workflow
1. Design the entities you'll need to manage
2. Devise the endpoints you need (think CRUD), grouping them into various route groups
3. Create placeholder controllers
4. Create placeholder routers, calling the placeholder controllers
5. Set up and test all routes in Postman
6. Create database
7. Set up DB connection string
8. Create models

