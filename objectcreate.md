# Object.create

Creates a new object with  \_\_proto\_\_ object set to

Takes two arguments:

1. The object to use as the prototype object
2. Properties to add to the object

```
var Alpha = function(name) {
  this.beta = 'abc';
}
var alphaInstance = new Alpha('Hello');

var createdInstance = Object.create(alphaInstance, {charlie: {value: 'def'}});

createdInstance.beta // abc
createdInstance.charlie // def
createdInstance.__proto__ === alphaInstance //true
```



