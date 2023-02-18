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

## Starting a TS Project
Create a TS project in the folder using the command below. It creates a `tsconfig.json` file.

```bash
npx tsc --init
```

Then, create a `dist` folder, enable, and modify the `ourDir` property:

```
"outDir": "./dist"
```

Then, create your entrypoint `index.ts`. To build, run:

```bash
npx tsc
```

This will compile your files and put them in `./dist`.