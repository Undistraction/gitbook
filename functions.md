# Functions

A function is an object, linked to `Function.prototype,` which is itself linked to `Object.prototype`. This means they can be treated like any other object and can be passed as arguments, returned, or stored in variables. They can also have their own methods.

A function has a `prototype` property. This property is not related to the prototype chain as it is on the object itself, not the `Function`object.

A function has three additional _hidden_ properties:

1. The `context` of the function
2. The code that implements its behaviour~code
3. `prototype` which stores its prototype object \(only relevant to constructor functions\).

A function can be invoked.

There are important differences between a _function declaration_ and a _function expression. _

### Function Declaration

A function declaration is a free-standing named function.

```
function alpha() {}
```

### Function Expression

A function expression is an anonymous function created with a literal that can be used where an expression is permissible. They are always either part of another statement, an argument or a return value.

```
function() {}
var alpha = function() {}
```

They can be immediately invoked.

```
(function(){})()
(function(){}())
```

_Note that the p\_arentheses_ around the function expression make it into an expression. without them it would be free-standing and therefore need a name, making it a function declaration.\_

When a function expression is immediately invoked it is known as an _IIFE_ \(immediately invoked function expression\) or an _immediate function._

### ES6 Arrow functions

ES6 introduces a simpler way to write a functional expression using the _fat arrow_ operator. If it is written without a function body, the expression on the right of the arrow is returned.

```
param => expression
```

This is equivalent to:

```
function(param) {
    return expression
}
```

Parentheses must be used if there are no params or more than one:

```
() => expression
(alpha, beta) => expression
```

If the body of the function is complex, a function body can be used, however in this case, an explicit return statement must be used to return a value:

```
param => {
    return expression;
}
```

## Closures

When a function is created, it retains a link to the context in which it is created. This is _closure_.

## Methods

When a function is stored as an attribute of an object it is known as a method. If it is invoked through the object, using dot notation, the `this` keyword will point to the object. Due to JavaScript's use of _Late Binding, \_this means that the this keyword can point to a different object \_depending on how the function was called._

```
var alpha = 'abc';

function beta() {
    return this.alpha;
}

var o1 = {
    alpha: 'def',
    beta: beta
}

var o2 = {
    alpha: 'ghi',
    beta: beta
}

beta() // 'abc'
o1.beta() // 'def'
o2.charlie() // 'ghi'
```

This leads to one of the biggest problems in JavaScript. When a function is called that is not a property of an object, it is bound to the global object, even if it is within a function with the context of an object.

```
var alpha = 'abc';

function beta(func) {

  var charlie = function() {
    return this.alpha;
  }

  return charlie();
}

var o1 = {
  alpha: 'def',
  beta: beta
}

beta(charlie) // 'abc'
```

However, variables defined in a function are visible to anything within it \(assuming they are not shadowed by another variable\), so the value of `this` can be stored in a variable for use by nested functions:

```
var alpha = 'abc';

function beta(func) {

  var that = this;

  var charlie = function() {
    return that.alpha;
  }

  return charlie();
}

var o1 = {
  alpha: 'def',
  beta: beta
}

beta(charlie) // 'def'
```

## Arguments

When a function is involked, a further parameter is made available: `arguments`, which contains all the arguments passed to the function, even if there were more values passed than the function has arguments. Although arguments does have a length property, it isn't an Array and lacks all of the other functionality of an Array.

