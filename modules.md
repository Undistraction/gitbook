# Modules

> A module is a function or object that presents an interface but that hides its state and the implementation.

Douglas Crockford, JavaScript: The Good Parts P40

A function can be used to establish a scope which will only be available to functions and properties that it defines.



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





