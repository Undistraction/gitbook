# Prototype

Firstly and most importantly, there are two related properties that are both referred to as `prototype`,  throughout documentation and writing on the subject. They are in fact two distinct properties that are related but fundamentally different.

1. The `__proto__` object, hidden on all objects.
2. The prototype attribute of the Function object.

## Useful Methods

To find an object's `__proto__`:

```
Object.getPrototypeOf(alpha);
```

To check if one object is the`__proto__`of another:

```
alpha.isPrototypeOf(beta);
```

## \_\_proto\_\_

which is hidden away, though can be accessed using `__proto__` in some browsers. This internal attribute _delegates_ to the object's prototype object for any methods that aren't on the object itself.

Note that you should never manipulate the `__proto__` \_ \_attribute in production code.

```
var grandparent = {
        alpha: 'abc'
    }

    var parent = {
        beta: 'def'
    }
    var child = {
        charlie: 'ghi'
    }

    parent.__proto__ = grandparent;
    child.__proto__ = parent;

    grandparent.alpha // 'abc'
    grandparent.beta // undefined
    grandparent.charlie // undefined

    parent.alpha // 'abc'
    parent.beta // 'def'
    parent.charlie // undefined

    child.alpha // 'abc'
    child.beta // 'def'
    child.charlie // 'ghi

    Object.getPrototypeOf(child) // {beta: 'def'}
    Object.getPrototypeOf(parent) // {alpha: 'abc'}
```

The`__proto__`attribute of a Function points to ???

The`__proto__`attribute of an instance points to the constructor function that created it.

## Function's prototype attribute

Function's `prototype` attribute is freely accessible using `Function.prototype`, and stores the methods used by the constructor function when constructing instances. When an instance is created from a constructor function, the instance's `__proto__`object is set to the Constructor function's `prototype` attribute.

