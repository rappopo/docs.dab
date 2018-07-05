---
description: Create or add a new document into a collection
---

# create

```javascript
create(body, params)
```

## Arguments

### Body \(required\)

Document body should be a plain javascript object. If ID is not provided, it'll be created automatically.

If collection has fields definition, than the document body will be sanitized according to its type. Columns that aren't listed in collection fields will also discarded. This is to make sure that you'll always get a clean and correct document saved in the database.

### Params \(required, mixed\)

A plain javascript object of:

* `collection`: Required, the name of collection you want to work with.
* `ignoreColumn`: If you want some columns to be ignored on validation process \(only in enforced attributes\), put its attribute id here. Optional, defaults to `[]`.

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

If the ID has been used before, it'll yield **Document already exists** error.

Any other error will yield a normal Node error object you can catch through promise easily.

