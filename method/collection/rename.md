---
description: Method to rename a collection.
---

# renameCollection

```javascript
renameCollection (oldName, newName, params)
```

## Arguments

### Old Name \(required\)

A string that indicate the existing collection name

### New Name \(required\)

A string for what the new collection will be named

### Params \(optional\)

* `withSchema`: optional, defaults to `false`. If set `true`, it'll try to rename the internal database while keeping its existing schema and data intact. In SQL database, this means: rename table

## Response

### Result

It should return an object like below:

```javascript
{
  success: true
}
```

### Error

It'll yield **Collection already exists** error if the new collection name has been used before. And **Collection not found** if the named collection is nowhere to be found.

Any other error will yield a normal Node error object you can catch through promise easily.

