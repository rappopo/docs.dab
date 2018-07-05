---
description: Find specific document by its **ID** throughout a collection.
---

# findOne

```javascript
findOne(id, params)
```

## Arguments

### ID \(required\)

Document ID to look for.

### Params \(required, mixed\)

A plain javascript object of:

* `collection`: Required, the name of collection you want to work with.

Or, you're also allowed to pass a string. In this case, it will be interpreted as the collection name.

## Response

### Result

It should return an object like the one below:

```javascript
{
  success: true,
  data: {
    _id: 'james-bond',
    name: 'James Bond',
    age: 40
    ...
  }
}
```

### Error

If no document found, it'll yield **Document not found** error.

Any other error will yield a normal Node error object you can catch through promise easily.

