# Functions

A function is an object, linked to `Function.prototype,` which is itself linked to `Object.prototype`. This means they can be treated like any other object and can be passed as arguments, returned, or stored in variables. They can also have their own methods.

A function has a `prototype` property. This property is not related to the prototype chain as it is on the object itself, not the `Function`object.

A function has two additional _hidden_ properties:

1. The `context` of the function
2. The code that implements its behaviour
3. `prototype`

A function can be invoked.

## Closures

When a function is created, it retains a link to the context in which it is created. This is _closure_.

## Methods

When a function is stored as an attribute of an object it is known as a method. If it is invoked through the object, using dot notation, the `this` keyword 



