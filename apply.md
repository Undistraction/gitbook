## Apply

As well as standard invocation and method invocation,  function can also be invoked using `apply` method. This allows:

1. The value of `this` within the the invoked function to be supplied.
2. Any  arguments to be supplied.

It is easier to think of it as being called `applyTo`.

_Note that the second argument must be an Array, even if it is a single value._

```
var alpha = 'abc';

function beta(value) {
  return value + this.alpha;
}

var o = {
  alpha: 'def',
  charlie: function(value) {
     return value + this.alpha;
  }
}

beta('Beta:') // Beta:abc
o.charlie('Charlie:') // Charlie:def

beta.apply(o, ['Beta:'])); // Beta:def
```

You are effectively saying 'Bind this function to the given object and call it with these arguments'.

