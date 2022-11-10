---
layout: default
title: Adjustments for TypeScript
nav_order: 2
parent: Express Projects
---

# Adjustments for TypeScript
{: .no_toc }

1. TOC
{:toc}

## Setup
Do the following as part of the setup for a TypeScript app:

- Generate `tsconfig` using `npx tsc --init`
- Enable `tsconfig`'s `outDir` setting and set it to `./dist` - this compiles your TypeScript code in that folder and runs `index.js` from there
- Change the scripts in `package.json`:
  - `"build": "npx tsc"`
  - `"start": "node dist/index.js"`
  - `"dev": "concurrently \"npx tsc --watch\" \"nodemon -q dist/index.js\""`
- Compile the app for the first time with `npm run build`
- You can now launch the dev server with `npm run dev` without any errors

## Working with Middleware
Middleware functions typically pass info down to the next middleware functions by adding properties to the `request` object. However, you can only do this in TypeScript by extending the `Request` type.

The way to do this in TypeScript is to extend the `Request` type:

1. In `src`, create a `types` folder with an `express` folder in it.
2. Create a file `index.d.ts` in the folder `types/express`.
3. Add your required properties in the `index.d.ts` file:

    ```ts
    declare namespace Express {
      interface Request {
        yourNewProperty?: string;
      }
    }
    ```

4. Add the `./types` (or `./src/types`) folder into the `typeRoots` option in `tsconfig.json`.

## Working Mongoose Model Methods
It is possible to define custom methods on Mongoose models in vanilla JavaScript. However, once again, you can only do this in TypeScript by creating interfaces for your model methods.

Process:

1. Create an interface for the model's methods.
    
    ```ts
    interface IUserMethods {
      getName(): string;
      createJWT(): string;
      checkPassword(candidatePassword: string): boolean;
    }
    ```

2. Create a model type that recognises both (1) the interface for the schema and (2) the interface for the method(s):

    ```ts
    type IUserModel = Model<IUserSchema, {}, IUserMethods>;
    ```

3. When defining the actual Mongoose `model`, specify the schema and type:

    ```ts
    const User = model<IUserSchema, IUserModel>('User', UserSchema)
    ```

For more examples, refer to the [Mongoose documentation on TypeScript](https://mongoosejs.com/docs/typescript/statics-and-methods.html).