---
description: Update an existing document in a collection.
---

# update

```javascript
update(id, body, params)
```

## Arguments

### ID \(required\)

The document ID.

### Body \(required\)

The new document body to be used as replacement.

If collection has fields definition, than the document body will be sanitized according to its type. Columns that aren't listed in collection fields will also discarded. This is to make sure that you'll always get a clean and correct document saved in the database.

### Params \(required, mixed\)

A plain javascript object of:

* `collection`: Required, the name of collection you want to work with.
* `ignoreColumn`: If you want some columns to be ignored on validation process, put its attribute id here. Optional, defaults to `[]`.
* `fullReplace`: If you want to have a full replacement, you should set it to `true`. Else it'll only update document partially. Optional, defaults to `false`

Or, you're also allowed to pass a string. In this case, it will be interpreted as the collection name and replacement mode is set to partial update.

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

