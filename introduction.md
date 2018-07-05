# Introduction

{% hint style="warning" %}
**All of these are for dummies only!!!** If you’re considered yourself as a javascript kungfu master, than you’d probably better to look for masterpieces like [Waterline](https://github.com/balderdashy/waterline) or [Sequelize](https://github.com/sequelize/sequelize) instead!!! 

But if you’re a dummy **like me**, then welcome to the party! Yay!! Finally a database access for fools!!! With lots of stuff and magic!!!!
{% endhint %}

## Background

Rappopo DAB is a set of conventions of database abstraction layer with focus on how to access and work with data easily. It won’t be a very sophisticated and overly complex library. On the contrary, it’ll only support the most basic operations. Not because I don’t need it, but simply because I’m too stupid & lazy to write such beast :\)

If you work with many different databases, be it relational or NoSQL one, you certainly have to face the same problem over and over again: different ways to access the data, learning its all new query language, etc. The list grows very quickly.

That’s why this project is born. It should helps lazy and stupid people like me to get more time to drink beer. Not learning a new alien stuff over and over again.

Existing libraries are way to complex for me. I only need the most basic ones: queryable through MongoDB-like query language, pagination mechanism. And a simple import & export data. Also, being a true fan of RESTful APIs, so why don’t I blindly steal their ways to find, create, update & remove documents? No more learning! And that means more time for beer!!

## Usage

**For developers**: this package gives you a basic class and guide lines on how to write package for some particular database. All you need to do is just extends this basic class and write methods according to its specification.

**For end user**: never use this package directly, because it won’t gives you anything other than headache! Instead, pick one of its implementation library chapter that match the database you want to work with.

If for some reason you want to change to another one later, the only thing you need to do is just requiring a different library and put its options correctly. Everything else should be the same.

Example \(development\):

```javascript
var Dab = require('@rappopo/dab-memory'),
  dab = new Dab()

dab.createCollection({ name: 'test' })
...

dab.find({ collection: 'test' }).then(function (results) => { ... })
```

And later in production, just change to this:

```javascript
var Dab = require('@rappopo/dab-couch'),
  dab = new Dab({ url: 'http://localhost:5984', dbName: 'mydb' })

// everything below this line should still be the same
dab.createCollection({ name: 'test' })
...

dab.find({ collection: 'test' }).then(function (results) => { ... })
```

