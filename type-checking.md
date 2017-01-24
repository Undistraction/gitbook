# Type Checking

For basic types:

```
function Delta() {}

var alpha = {}
var beta = 'abc';
var charlie = new String('abc');
var delta = new Delta();

typeof alpha === 'object' // true
typeof beta === 'string' // true
typeof charlie === 'string' // true
typeof delta === 'object' // true
```

Using the constructor function indirectly. Note this will return true if there is a constructor function of that type anywhere in the object's prototype chain, not just if it is that object's constructor:

```
alpha instanceof Object // true
beta instanceof String // false (This is a primitive form of string).
charlie instanceof String // true (This is an object form)
delta instanceof Delta // true
```

Using the constructor function directly:

```
alpha.constructor === Object // true
beta.constructor === String // true
charlie.constructor === String // true
delta.constructor === Delta // true
```



