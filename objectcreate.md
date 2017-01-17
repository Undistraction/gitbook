# Object.create

Takes two arguments:

1. The object to use as the prototype object
2. Properties to add to the object

```
var Alpha = function(name) {
  this.beta = 'abc';
}
var alphaInstance = new Alpha('Hello');

var b = Object.create(alphaInstance, {charlie: {value: 'def'}});

b.beta // 'abc'
b.charlie // 'def'
```



