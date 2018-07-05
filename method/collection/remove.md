---
description: Method to remove a collection.
---

# removeCollection

```javascript
removeCollection(name, params)
```

## Arguments

### Name \(required\)

A string that indicate which collection to be removed

### Params \(optional\)

* `withSchema`: optional, defaults to `false`. If set `true`, it'll destroy both the internal schema and data for good.

## Response

### Result

It should return an object like below:

```javascript
{
  success: true
}
```

### Error

It'll yield **Collection not found** if the named collection is nowhere to be found.

Any other error will yield a normal Node error object you can catch through promise easily.

