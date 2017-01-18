#ES2016 bind

Using bind creates a new function for which the value of `this` is set to the
object passed. This means that rather than `this` referring to object calling
the function, it will refer to object passed. For example if an event handler
is fired, if the handler has been bound, the scope of the handler will be set
to the bound object.

```
this.linkClicked = this.linkClicked.bind(this);
```
