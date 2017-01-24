# Classes

Under the hood, classes are just standard objects.

```
function Alpha(beta) {
  this.beta = beta;
}

Alpha.prototype.charlie = function() {}


class Delta {
  
  constructor(beta) {
    this.beta = beta
  }
  
  charlie() {}
}

var alpha = new Alpha('abc');
var delta = new Delta('abc');

console.log(alpha); // Alpha {beta: 'abc'}
console.log(delta); // Delta {beta: 'abc'}
console.log(alpha.charlie) // Function
console.log(delta.charlie) // Function
console.log(alpha.constructor) // Constructor function
console.log(delta.constructor) // Class
```

### Static Methods

A static method is a method on the class rather than an instance of that class. This can be achieved using the `static` keyword.

```
class Alpha {
  
  constructor(beta) {
    this.beta = beta
  }
  
  charlie() {}
  
  static delta() {}
}

var alpha = new Alpha('abc');

console.log(alpha.delta) // undefined
console.log(Alpha.delta) // Function
```



