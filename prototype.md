# Prototype

Firstly and most importantly, there are two related properties that are both referred to as `prototype`,  throughout documentation and writing on the subject. They are in fact two distinct properties that are related but fundamentally different.

1. The `__proto__` object, hidden on all objects.
2. The prototype attribute of the Function object.

## \_\_proto\_\_

which is hidden away, though can be accessed using `__proto__` in some browsers. This internal attribute points to the object's prototype object from which it receives methods.

\`\`\`

var grandparent = {

alpha: 'abc'

}

var parent = {  
  beta: 'def'  
}

var child = {  
  charlie: 'ghi'  
}

parent.**proto** = grandparent;  
child.**proto** = parent;

grandparent.alpha // 'abc'  
grandparent.beta // undefined  
grandparent.charlie // undefined

parent.alpha // 'abc'  
parent.beta // 'def'  
parent.charlie // undefined

child.alpha // 'abc'  
child.beta // 'def'  
child.charlie // 'ghi  
\`\`\`

## Function's prototype attribute

Function's `prototype` attribute is freely accessible using `Function.prototype`, and stores the methods used by the constructor function when constructing instances.

