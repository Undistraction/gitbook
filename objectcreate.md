# Object.create

Creates a new object with  \_\_proto\_\_ object set to the supplied object

Takes two arguments:

1. The object to use as the prototype object
2. Properties to add to the object

```
var alphaObject = {
  beta: 'abc'
}

var createdInstance = Object.create(alphaObject, {charlie: {value: 'def'}});

createdInstance.echo = function() {
  return this.beta + this.charlie;
}

createdInstance.echo() // 'abcdef'
createdInstance.__proto__ === alphaObject // true
```

Example using an object instance from a custom constructor function

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



