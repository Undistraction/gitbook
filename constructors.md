# Constructor Functions

When a function is invoked using the `new` keyword, it becomes a _constructor function_ and behaves differently, returning a new Object.

_Note: It is customary to capitalise the name of a constructor function:_

```
var Alpha = function() {}

new Alpha(); // Object {}
```

The this keyword points to the object that is being created, so attributes added using this will be added to the constructed object.

```
var Alpha = function() {
    this.beta = 'abc';
}

new Alpha(); // Object { beta: 'abc' }
```

Methods can be added to the constructed object through its `prototype` attribute:

```
var Alpha = function() {
    this.beta = 'abc';
}

Alpha.prototype.charlie = function() {
   return this.beta;
}

new Alpha().charlie(); // abc
```

A constructor function should never be called without the `new` keyword.

Although it might appear more compact to add methods to the prototype within the constructor function itself, this would be inefficient, as each call to the constructor would recreate the same method and re-add it to the prototype. By adding the method to the prototype outside of the constructor, it is added one time only.

