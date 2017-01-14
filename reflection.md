# Reflection

The type of an object can be revealed using the _operator_ `typeof`:

```
var alpha = 'abc';
var bravo = 2;
var charlie = {};

typeof alpha; // 'string'
typeof bravo; // 'number'
typeof charlie; // 'object'
```

This can also be used on an object:

```
var o = {
    alpha: 'abc',
    bravo: 2,
    charlie: {}
}

typeof o.alpha; // 'string'
typeof o.bravo; // 'number'
typeof o.charlie; // 'object'
```

However, there is no distinction between variables and functions as both are properties of the object.

```
var o = {};
typeof o.toString  // 'function'
```

The function hasOwnProperty can be used to check if the property was defined on the object \(and not in its prototype chain\):

```
var o = {};
o.hasOwnProperty('toString');  // 'false'
```





