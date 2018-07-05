---
description: Validate data input
---

# Validator

Validation is a way to validate document. That being said, for example, if a column is declared to be an email, it should also have correct format.

DAB **won't** automatically validate a document. You must execute it manually using [`dab.validateDoc()`](../method/misc/validate-doc.md) call.

DAB will try to validate document if:

* Its schema collection \(i.e: `attributes`\) isn't empty
* Explicitly defined in `validator` options

All [validator.js method](https://github.com/chriso/validator.js#validators) are supported:

| Validator | Description |
| --- | --- |
| `contains: "<seed>"` | Check if value contains the seed |
| `equals: "<comparison>"` | Check if value matches the comparison |
| `isAfter: true` or `isAfter: "<dt> [, <format>]"` | Check if value is a date that's after `now` or after `dt` in moment.js specified format |
| `isAlpha: true` or `isAlpha: "<locale>"` | check if value contains only letters \(a-zA-Z\) in `en-US` or [specific locale](https://github.com/chriso/validator.js#validators) |
| `isAlphanumeric: true` or `isAlphanumeric: "<locale>"` | check if value contains only letters and numbers in `en-US` or [specific locale](https://github.com/chriso/validator.js#validators) |
| `isAscii: true` | Check if the string contains ASCII chars only |
| `isBase64: true` | check if a string is base64 encoded |
| `isBefore: true` or `isBefore: "<dt> [, <format>]"` | Check if value is a date that's before `now` or before `dt` in moment.js specified format |
| `isBoolean: true` | check if a string is a boolean |
| `isByteLength: true` or `isByteLength: {...}` | check if the string's length \(in UTF-8 bytes\) falls in a range |
| `isCreditCard: true` | check if the string is a credit card |
| `isCurrency: true` or `isCurrency: {...}` | check if the string is a valid currency amount. [More on options](https://github.com/chriso/validator.js#validators) |
| `isDataURI: true` | check if the string is a data uri format |
| `isDecimal: true` or `isDecimal: {...}` | check if the string represents a decimal number. [More on options](https://github.com/chriso/validator.js#validators) |
| `isDivisibleBy: <number>` | check if the string is a number that's divisible by another |
| `isEmail: true` or `isEmail: {...}` | check if the string is an email. [More on options](https://github.com/chriso/validator.js#validators) |
| `isEmpty: true` | check if the string has a length of zero |
| `isFQDN: true` or `isFQDN: {...}` | check if the string is a fully qualified domain name. [More on options](https://github.com/chriso/validator.js#validators) |
| `isFloat: true` or `isFloat: {...}` | check if the string is a float. [More on options](https://github.com/chriso/validator.js#validators) |
| `isFullWidth: true` | check if the string contains any full-width chars |
| `isHalfWidth: true` | check if the string contains any half-width chars |
| `isHash: "<algorithm>"` | check if the string is a hash of type algorithm. [More on algorithm](https://github.com/chriso/validator.js#validators) |
| `isHexColor: true` | check if the string is a hexadecimal color |
| `isHexadecimal: true` | check if the string is a hexadecimal number |
| `isIP: true` or `isIP: "<version>"` | check if the string is an IP. `version` = 4 or 6 |
| `isISBN: true` or `isISBN: "<version>"` | check if the string is an ISBN. `version` = 10 or 13 |

