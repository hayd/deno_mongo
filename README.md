# deno_mongo

> **deno_mongo** is a **MongoDB** database driver developed for deno, based on rust's official [`mongodb`](https://crates.io/crates/mongodb) library package.

[![tag](https://img.shields.io/github/tag/manyuanrong/deno_mongo.svg)](https://github.com/manyuanrong/deno_mongo/releases)
[![Build Status](https://github.com/manyuanrong/deno_mongo/workflows/ci/badge.svg?branch=master)](https://github.com/manyuanrong/deno_mongo/actions)
[![license](https://img.shields.io/github/license/manyuanrong/deno_mongo.svg)](https://github.com/manyuanrong/deno_mongo)
[![tag](https://img.shields.io/badge/deno-v0.35.0-green.svg)](https://github.com/denoland/deno)

## Links

- [Guides]() TODO
- [Examples]() TODO
- [Benchmarks]() TODO

## Examples

```ts
import { init, MongoClient } from "https://deno.land/x/mongo@v0.3.2/mod.ts";

// Initialize the plugin
await init();

const client = new MongoClient();
client.connectWithUri("mongodb://localhost:27017");

const db = getClient().database("test");
const users = db.collection("users");

// insert
const insertId = await users.insertOne({
  username: "user1",
  password: "pass1"
});

// insertMany
const insertIds = await users.insertMany([
  {
    username: "user1",
    password: "pass1"
  },
  {
    username: "user2",
    password: "pass2"
  }
]);

// findOne
const user1 = await users.findOne({ _id: insertId });

// find
const users = await users.find({ username: { $ne: null } });

// updateOne
const { matchedCount, modifiedCount, upsertedId } = await users.updateOne(
  username: { $ne: null },
  { $set: { username: "USERNAME" } }
);

// updateMany
const { matchedCount, modifiedCount, upsertedId } = await users.updateMany(
  username: { $ne: null },
  { $set: { username: "USERNAME" } }
);

// deleteOne
const deleteCount = await users.deleteOne({ _id: insertId });

// deleteMany
const deleteCount2 = await users.deleteMany({ usename: "test" });
```
