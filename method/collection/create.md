---
description: Method to create a collection.
---

# createCollection

```javascript
createCollection(definition, param)
```

## Arguments

### Definition \(required\)

Collection definition is a plain javascript object. In its simples form, it only needs a `name`:

* `name`: a unique name to identify the collection. Required.
* `attributes`: an object of column definitions. Optional.

Take a look at the example below:

```javascript
{
  name: 'users',
  attributes: {
    _id: 'string',
    username: { type: 'string', length: 20, { validator: { required: true }}},
    email: { type: 'string', length: 50, { validator: { required: true, isEmail: true }}},
    fullname: { type: 'string', { validator: { required: true }}},
    admin: { type: 'boolean', { validator: { required: true }}, default: false },
    age: 'integer'
  }
}
```

Supported column types: `string`, `integer`, `float`, `boolean`, `text`, `date`, `datetime`.

If you put a text value instead an object in a column, it'll automatically be translated as its column type.

For some types like: `integer`, `float`, `boolean`, `date`, and `datetime`, it'll automatically put the right [validator](../../features/validator.md) and [sanitizer](../../features/sanitizer.md) into account.

To hide some columns from result set, use `hidden` property and set it to `true`

To transform the key to something else, use `mask` property and set it to any key name.

Example:

```javascript
...
// internally saved as this:
[
  { _id: 'james-bond', name: 'James Bond', gender: 'Male', age: 45 },
  { _id: 'jason-bourne', name: 'Jason Bourne', gender: 'Male', age: 36 },
  ...
]
...
// with this fields definition:
{
  name: 'agents',
  attributes: {
    _id: { type: 'string', mask: 'code' },
    name: { type: 'string', mask: 'fullName' },
    gender: { type: 'string', mask: 'sex' },
    age: { type: 'integer', hidden: true }
  }
}
...
// and execute this method:
dab.find({ collection: 'agents' })
...
// will return this result set:
{
  success: true,
  data: [
    { code: 'james-bond', fullName: 'James Bond', sex: 'Male' },
    { code: 'jason-bourne', fullName: 'Jason Bourne', sex: 'Male' },
    ...
  ]
}
```

You can also add column [validators](https://github.com/rappopo/books.dab/tree/a7385934c5a25d9345372dc318a6f1a90953e1f1/dab/feature/validator/README.md) & [sanitizers](https://github.com/rappopo/books.dab/tree/a7385934c5a25d9345372dc318a6f1a90953e1f1/dab/feature/sanitizer/README.md). These will guarantee that whatever you put in the database are in correct types and values.

### Params \(optional\)

* `withSchema`: optional, defaults to `false`. If set `true`, it'll destroy its internal database schema and rebuild a new one. In SQL database, this means **very dangerous**: drop existing table and recreate a new one with a schema built from the fields definition. All existing records & schema will be lost forever.

## Response

### Result

It should return an object like below:

```javascript
{
  success: true
}
```

### Error

It'll yield **Collection already exists** error if the collection name has been used before.

Any other error will yield a normal Node error object you can catch through promise easily.

