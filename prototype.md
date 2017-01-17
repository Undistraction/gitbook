# Prototype Chain

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

To find the name of a `__proto__` 's constructor:

```
__proto__.constructor.name
```

## \_\_proto\_\_

This internal attribute stores a _prototype object_. The object was given to it at construction time and is the same object referenced by the Constructor function's `prototype` attribute _delegates_ to the object's prototype object for any methods that aren't on the object itself.

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

The `__proto__` attribute of a constructor function points to the prototype object stored in the prototype attribute of the Function constructor.

The`__proto__`attribute of an instance points to the object stored in the `prototype` attribute of the constructor function that created it.

The `__proto__` attribute of a prototype object points to the next prototype object in the chain.

## Function's prototype attribute

A function has its own `prototype` attribute. Constructor functions therefore also have this attribute. However the objects that they construct do not, not being Functions.

The `prototype` attribute stores an object. This object has the following attributes:

1. `constructor` This is a reference back to the constructor function.
2. `__proto__` This is just the generic  `__proto__` attribute that all objects possess - This is an object so it points to the Object constructor function's prototype attribute.

3. Any other attributes

## Relationship between `__proto__` and Functions' prototype attribute

When a constructor function creates an instance, it sets the instance's `__proto__` attribute to its own prototype attribute.

![](/assets/prototype-chain-01.jpg)

## Delegation

When the compiler looks up an attribute on an object instance, it first looks at the object itself, then at the object stored in its `__proto__` attribute. If it still hasn't found the attribute it will look at the `__proto__` attribute of this object and so on until the attribute is discovered or the value of `__proto__` is `undefined`.





