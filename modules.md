# Modules

> A module is a function or object that presents an interface but that hides its state and the implementation.

_Douglas Crockford, JavaScript: The Good Parts P40_

A function can be used to establish a scope which will only be available to functions and properties that it defines.

Here is an example using an object, so that the object has private attributes.

```
function createModule() {
    var alpha = 'abc';

    return {
        getAlpha: function() {
            return alpha;
        }
    }
}



var module = createModule();

module.getAlpha() // 'abc'
module.alpha // undefined
```

Here is an example using a function so that the function has access to private attributes

```
function createModule() {
    var alpha = 'abc';

    var beta = function() {
        return alpha;
    }

    return beta;
}

var beta = createModule();
beta() // 'abc'
beta.alpha // undefined
```
