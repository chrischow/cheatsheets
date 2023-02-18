---
layout: default
title: Getting Started
nav_order: 1
parent: TypeORM
---

# Getting Started
{: .no_toc }

1. TOC
{:toc}

## Starting a TypeORM Project
Start a project with this command:

```bash
npx typeorm init --name MyProject --database postgres
```

Settings to amend in `tsconfig.json`:

```
"experimentalDecorators": true
"emitDecoratorMetadata": true
"strictPropertyInitialization": false
```