---
description: >-
  Query specific document from selected database using MongoDB-like query
  language.
---

# find

```javascript
find(params)
```

## Arguments

### Params \(required\)

As parameter, pass the following object:

* `collection`: Required, the name of collection you want to work with.
* `query`: query in MongoDB-style query syntax. Optional, defaults to: `{}` \(match all\).
* `sort`: sort order, as a [string](../../features/sort-order.md#as-string), [array](../../features/sort-order.md#as-array) or [object](../../features/sort-order.md#as-object). Optional. Example:

  ```javascript
    { name: 1, age: -1 }
  ```

* `limit`: max. number of documents in one page. Optional, defaults to `25`. Overridable through [options](../misc/set-options.md) object.
* `page`: page number, starting from 1. Optional, defaults to 1

Example:

```javascript
{
  collection: 'users',
  query: {
    age: { $gt: 20 }
  },
  page: 1,
  limit: 25
}
```

## Response

### Result

It should return an object like below:

```javascript
{
  success: true,
  total: 120,
  data: [
    { _id: 'james-bond', name: 'James Bond', age: 20 },
    { _id: 'jack-bauer', name: 'Jack Bauer', age: 20 },
    { _id: 'jason-bourne', name: 'Jason Bourne', age: 20 },
    ...
  ]
}
```

If no document found, it should **NOT** yield error. Instead, it sould return an empty data with total = 0.

`total` is the total number of documents found matched with your query. Optional, but strongly recommended to return this value.

### Error

In case of error, it'll yield a normal Node error object you can catch through promise easily.

