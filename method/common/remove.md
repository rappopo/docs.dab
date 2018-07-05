---
description: Remove an existing document from a collection.
---

# remove

```javascript
remove (id, params)
```

## Arguments

### ID \(required\)

The document ID.

### Params \(required, mixed\)

A plain javascript object of:

* `collection`: Required, the name of collection you want to work with.
* `withSource`: If you want to get the related document before deleted, set it to `true`. The document will be put under `source` key. Optional, defaults to `false`

Or, you're also allowed to pass a string. In this case, it will be interpreted as the collection name.

## Response

### Result

It should return an object like the one below:

```javascript
{
  success: true
}
```

And with `withSource` set to _true_:

```javascript
{
  success: true,
  source: {
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

