# Reflection

The type of an object can be revealed using `typeof`:

```
var alpha = 'abc';
var bravo = 2;
var charlie = {};

typeof(alpha); // 'string'
typeof(bravo); // 'number'
typeof(charlie); // 'object'
```

This can also be used on an object:

```
var o = {
    alpha: 'abc',
    bravo: 2,
    charlie: {}
}

typeof(o.alpha); // 'string'
typeof(o.bravo); // 'number'
typeof(o.charlie); // 'object'
```

However, there is no distinction between variables and functions as both are properties of the object.

```
var o = {};
typeof(o.toString) // 'function'
```



