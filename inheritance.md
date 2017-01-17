# Inheritance

Inheritance provides two advantages:

1. Allows code to be reused, so that only the differences need to be specifies instead of all the similarities repeated.
2. Allows specification of Types

## **Prototype Objects**

1. All objects have a `constructor` attribute that they have inherited through the prototype chain from Object.prototype.constructor.

2. All objects have a `__proto__` attribute.

This means that any object can replace a Function's `prototype` attribute.

By setting a constructor's prototype attribute to the instance of an object,  the attributes of that object become available to any object instances constructed from it.

## Differential Inheritance

Customisation of a new object by specifying the differences from the object on which it is based.

Note: Object.create sets the new object's `__proto__` object to the supplied object, meaning it gains the attributes of that object.

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

## Using Functions For Privacy

Through the use of functions / closure, an object can be constructed with completely private attributes:

```
var alphaConstructor = function() {
  
  var beta = 'abc';
  
  var getBeta = function() {
    return beta;
  }
  
  return {
    getBeta: getBeta
  }
}

var alphaObject = alphaConstructor();

alphaObject.getBeta() // 'abc'
alphaObject.beta // undefined 
```

This can be taken further by storing private attributes on an object that is passed into the constructor or created. That way, one constructor can pass a secret object in to another constructor. In this way, private attributes can be shared between chained constructors.

```
var alphaConstructor = function(privateObject) {
  
  privateObject = privateObject || {};
  
  privateObject.beta = privateObject.beta || 'abc';
  
  var getBeta = function() {
    return privateObject.beta;
  }
  
  return {
    getBeta: getBeta
  }
}

var alphaObject = alphaConstructor();

var charlieConstructor = function(privateObject) {
  
  privateObject = privateObject || {};
  
  privateObject.beta = 'def';
  privateObject.delta = 'ghi';
  
  var getDelta = function() {
    return privateObject.delta;
  }
  
  var o = alphaConstructor(privateObject);
  
  o.getDelta = getDelta;
  
  return o;
  
}

var charlieObject = charlieConstructor();

console.log(alphaObject.getBeta()) // 'abc'
console.log(charlieObject.getBeta()) // 'def'
console.log(charlieObject.getDelta()) // 'ghi'
```



