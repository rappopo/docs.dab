---
description: Data & parameter sanitizer
---

# Sanitizer

Every document that goes to the database needs to be sanitized first. This is to ensure that the document is properly saved according its schema definition.

If schema collection is provided \(i.e: `attributes` isn't empty\), then on every `create()` and `update()` operation the body parameter is automatically sanitized:

1. According to its type: `boolean`, `date`, `datetime`, `float`, and `integer` will automatically sanitized using its related sanitizer.
2. According to its sanitizer definition below.
3. You can put one or more sanitizer on every attributes. Sanitizers put manually on attributes will override the one automatically provided according to its type.

Example:

```javascript
...
createCollection({
  name: 'users',
  attributes: {
    username: {
      type: 'string',
      sanitizer: {
        trim: true,
        blacklist: '12345'
      }
    },
    name: {
      type: 'string',
      sanitizer: {
        trim: true
      }
    },
    gender: {
      type: 'boolean'
    },
    birth_date: {
      type: 'date',
      sanitizer: {
        toDate: 'YYYY-MM-DD'
      }
    },
    email: {
      type: 'string',
      sanitizer: {
        normalizeEmail: {
          all_lowercase: false
        }
      }
    }
    ...
  }
})
...
```

From the example above:

* `username` will be trimmed from whitespace and accept any character except 1, 2, 3, 4 and 5
* `name` will be trimed from whitespace
* `gender` will be converted using `toBoolean` sanitizer
* `birth_date` will be parsed using `YYYY-MM-DD` pattern
* `email` will be sanitized using `normalizeEmail` with custom options

If error occurs, or value doesn't match the provided pattern, value will be converted to `null`

All [validator.js sanitizers](https://github.com/chriso/validator.js#sanitizers) are supported:

| Sanitizer | Description \(cited from validator.js\) |
| --- | --- |
| `blacklist: "<chars>"` | Remove characters that appear in the blacklist |
| `escape: true` | Replace `<`, `>`, `&`, `'`, `"` and `/` with HTML entities |
| `unescape: true` | Replace HTML encoded entities with `<`, `>`, `&`, `'`, `"` and `/` |
| `ltrim: true` or `ltrim: "<chars>"` | Trim characters from the left-side |
| `normalizeEmail: true` or `normalizeEmail: {...}` | Canonicalizes an email address. [More...](https://github.com/chriso/validator.js#sanitizers) |
| `rtrim: true` or `rtrim: "<chars>"` | Trim characters from the right-side |
| `stripLow: true` | Remove characters with a numerical value &lt; 32 and 127, mostly control characters |
| `toBoolean: true` | Convert everything that isn't `1` or `true` to `false`. |
| `toDate: true` or `toDate: "<format>"` | Convert to a date. Format is one of moment.js supported format |
| `toDatetime: true` or `toDatetime: "<format>"` | Convert to a datetime.Format is one of moment.js supported format |
| `toFloat: true` | Convert to a float |
| `toInteger: true` | Convert to an integer |
| `trim: true` or `trim: "<chars>"` | Trim characters \(whitespace for `true`\) from both sides |
| `whitelist: "<chars"` | Remove characters that do not appear in the whitelist |

