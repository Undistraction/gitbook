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

The`__proto__`attribute of an instance points to the object stored in the `prototype` attribute of the constructor function that created it. 

## Function's prototype attribute

A function has its own `prototype` attribute. Constructor functions therefore also have this attribute. However the objects that they construct do not, not being Functions.

The `prototype` attribute stores an object. This object has the following attributes:

1. `constructor` This is a reference back to the constructor function.
2. `__proto__` This is a reference to the prototype object of the constructor function itself.

3. Any other attributes

## Relationship between `__proto__` and Functions' prototype attribute

When a constructor function creates an instance, it sets the instance's `__proto__` attribute to its own prototype attribute.

