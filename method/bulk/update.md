---
description: Method for updating many documents in one shot.
---

# bulkUpdate

```javascript
bulkUpdate(body, param)
```

{% hint style="warning" %}
Due to the complexity and effectiveness, it is **always** a replace operation. Meaning the whole document body, except the id, will be replaced with the new one provided.

Partial updates are not supported.
{% endhint %}

## Arguments

### Body \(array, required\)

Body is always an array of objects. Every object needs to have an **ID**, otherwise, it'll yield a _Not found_ error. Example:

```javascript
[
  { _id: 'james-bond', name: 'James Bond 007' },
  { _id: 'jack-bauer-001', name: 'Mr. Jack Bauer' },
  { name: 'Johnie Englesh' }   // id isn't provided here, it'll yield an error
  ...
]
```

### Params \(required\)

* `collection`: Required, the name of collection you want to work with.
* `withDetail`: default is _false_. If _true_, details of operation will be returned. It is an array of objects in the same order as body request above. See example below.

## Response

Method should always return a response, eventhough one or more update could fail. If failed, those corresponding rows should tell why it failed, assuming it is enabled through `withDetail` parameter above.

The order of update result should match with the order of body request.

Promise rejection error should only occour when something very bad happened within the script.

Example:

```javascript
{
  success: true,
  stat: {
    ok: 1,
    fail: 2,
    total: 3
  },
  detail: [
    { _id: 'james-bond', success: true },
    { _id: 'jack-bauer-001', success: false, message: 'Document not found' },
    { _id: '337b116d-650e-4581-8bef-7b119467b05c', success: false, message: 'Document not found' }
  ]
}
```

