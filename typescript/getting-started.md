---
layout: default
title: Getting Started
nav_order: 1
parent: TypeScript
---

# Getting Started
{: .no_toc }

1. TOC
{:toc}


## Starting a Node.js Project with TypeScript
We assume that you're using a Node.js project. To set up a Node.js project with TypeScript:

- `nodemon`: For re-running your `index.js` script
- `tsc`: TypeScript
- `@types/node`: Types for node

```bash
# Initialise project
npm init

# Install dev dependencies
npm install --save-dev nodemon tsc @types/node
```

Initialise TypeScript using the command below. It creates a `tsconfig.json` file.

```bash
npx tsc --init
```

Then, create a `dist` folder, enable the `outDir` property in `tsconfig.json`, and modify it:

```
"outDir": "./dist"
```

This will let TypeScript know to compile your files and put them in `./dist`.

Then, add a run script to `package.json` to watch your TypeScript files, re-compile when changes are made to them, and re-run the compiled `index.js`:

```
"start": "tsc -w & nodemon ./dist/index.js"
```
