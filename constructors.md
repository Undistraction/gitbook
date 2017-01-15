# Constructors

When a function is invoked using the `new` keyword, it becomes a _constructor function_ and behaves differently.

```
var alpha = new Alpha();
```

A constructor is a normal function with a capitalised name \(by convention\):

```
var Alpha = function() {}
```

As with any object, they can define their own properties:

```
var Alpha = function() {
    this.beta 'abc'
}
```



