# Constructors

When a function is invoked using the `new` keyword, it becomes a _constructor function_ and behaves differently.

```
var alpha = new Alpha();
```

It is customary to capitalise the name of a constructor function:

```
var Alpha = function() {}
```

They can define their own properties:

```
var Alpha = function() {
    this.beta = 'abc';
}
```



