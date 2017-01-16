# Prototype

Firstly and most importantly, there are two related properties that are both referred to as `prototype`,  throughout documentation and writing on the subject. They are in fact two distinct properties that are related but fundamentally different.

1. The `__proto__` object which is hidden away, though can be accessed using `__proto__` in some browsers. This internal attribute points to the object's prototype object from which it receives methods.
2. The prototype attribute of the Function object, freely accessible using Function.prototype, and storing the methods of the object.

## \_\_proto\_\_

```
var grandparent = {
  alpha: 'abc'
}

var parent = {
  beta: 'def'
}

var child = {
  charlie: 'ghi'
}

parent.__proto__ = grandparent;
child.__proto__ = parent;

console.log(grandparent.alpha);
console.log(grandparent.beta);
console.log(grandparent.charlie);

console.log(parent.alpha);
console.log(parent.beta);
console.log(parent.charlie);

console.log(child.alpha);
console.log(child.beta);
console.log(child.charlie);
```



