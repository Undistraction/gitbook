# Objects

## Simple Types

* Numbers \(including `NaN`\)
* Strings
* Booleans \(`true`/`false`\)
* `null`
* `undefined`

Everything else is an object.

## Objects

Objects are always passed around by reference.

### Keys

Keys must be Strings. If they are not Strings, they will be transformed into Strings.

If an object is used as a key, it will be transformed into a string.

    var alpha = {};
    var beta = {};
    var charlie = {};

    alpha[beta] = 'abc';

    // Key will be "[object Object]"

    alpha[beta] // 'abc'

    // This works because again, the object `beta` is converted to [object Object]

    alpha[charlie] // 'abc'

    // This works even though it is a different object, because it is also converted to [object Object]

However, if it is added as a key to an object literal, its name will be treated as a string:

```
var alpha = {}
var beta = {
    alpha: 'abc'
}

beta[alpha] // undefined
beta['alpha'] // 'abc'
```

Keys for object literals must be wrapped in a string if they don't satisfy the same rules as variable names.

```
{
    alpha-beta: 'abc'
}

// Error

{
    'alpha-beta': 'abc'
}

// OK
```

## Access

Accessing a key that doesn't exist will return  `undefined`.

To set a value if none already exists:

```
var alpha = beta[charlie] || 'delta';
```

Attempting to access a value from `undefined`will result in a _Type Error_ exception. This can be guarded against using:

```
var alpha = beta[charlie] && beta[charlie].delta
alpha // undefined (but no exception is raised)
```



