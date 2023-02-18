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

## Pre-requisites
You should have TypeScript (`tsc`) and Nodemon (`nodemon`) installed globally:

```bash
npm install -g tsc nodemon
```

## Starting a TS Project
Create a TS project in the folder using the command below. It creates a `tsconfig.json` file.

```bash
npx tsc --init
```

Then, create a `dist` folder, enable the `outDir` property in `tsconfig.json`, and modify it:

```
"outDir": "./dist"
```

Then, create your entrypoint `index.ts`. To build, run:

```bash
npx tsc
```

This will compile your files and put them in `./dist`. You can now run the compiled JS file with:

```bash
npx ./dist/index.js
```

## Running TS Code with Node
You'll need to create a Node.js project, and install the types for TypeScript:

```bash
npm init
npm install --save-dev @types/node
```

Then, add a run script to `package.json` to watch your TypeScript files, re-compile when changes are made to them, and re-run the compiled `index.js`:

```
"start": "tsc -w & nodemon ./dist/index.js"
```
