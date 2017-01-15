## Apply

As well as standard invocation and method invocation,  function can also be invoked using `apply` method. This allows:

1. Any number of arguments to be supplied.
2. The value of `this` within the the invoked function to be supplied.

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

console.log(beta.apply(o, ['Nums:']));
```



