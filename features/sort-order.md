---
description: On how to achieve sorted results
---

# Sort Order

To get sorted results on [find\(\)](../method/common/find.md), you can put `sort` option as parameter. The following rules apply:

### As String

This is the most simplest one: put the column name to sort on that column. E.g:

```javascript
dab.find({ sort: 'name' })
```

To sort on multiple columns, use comma \(","\) as separator. Like this:

```javascript
dab.find({ sort: 'name, age' })
```

What about sort direction? Easy peasy:

```javascript
dab.find({ sort: 'name asc, age desc' })
```

### As Array

You can also put sort option as array, like these examples below:

```javascript
dab.find({ sort: ['name'] })
dab.find({ sort: ['name', 'age'] })
```

For sort order, wrap it as object and make the column name as the key while the direction being its value:

```javascript
dab.find({ sort: [
  { name: 'asc' },
  { age: 'desc' }
] })
```

You can also use MongoDB-like syntax for sort order: 1 for ascending, -1 for descending order. You may also mix and match any style above:

```javascript
dab.find({ sort: [
  'name',
  { age: -1 },
  { gender: 'asc' }
] })
```

### As Object

The preferred way to express sort order in Dab. Clean & expressive:

```javascript
dab.find({ sort: {
  name: 1,
  age: -1,
  gender: 'asc'
}} )
```

