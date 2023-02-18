---
layout: default
title: Patterns
nav_order: 2
parent: TypeORM
---

# Patterns
{: .no_toc }

1. TOC
{:toc}

## Manager Pattern
Use the manager object from the DataSource object.

```ts
import { AppDataSource } from "./data-source"
import { User } from "./entity/User"

// Create
const user = new User()
user.name = "Timber"
user.age = 25
await AppDataSource.manager.save(user)

// Read all users
const users = await AppDataSource.manager.find(User)

// Find by ID
const firstUser = await myDataSource.manager.findOneBy(User, {
    id: 1,
})
```

## Repository Pattern

```ts
const userRepository = AppDataSource.getRepository(User)

// Create
const user = new User()
user.firstName = "Timber"
user.lastName = "Saw"
user.age = 25
await userRepository.save(user)

// Create (alternate)
// const user = userRepository.create({ firstName: 'Timber', lastName: 'Saw', age: 25 })
// await userRepository.save(user)

// Read all users
const users = await userRepository.find()

// Find by ID
const firstUser = await userRepository.findOneBy({
    id: 1,
})
```