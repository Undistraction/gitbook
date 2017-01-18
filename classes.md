# Classes

## Class Definition

```
class Example {

  constructor(alpha, beta) {
    this.alpha = alpha;
    this.beta = beta;
  }

  instanceMethod() {
    // Can access this.alpha
  }

}

let c = new Example('alpha', 'beta');
```

## Subclass

```
class ExampleSubclass extends Example {

  constructor(alpha, beta, charlie) {
    super(alpha, beta);
  }

  anotherInstanceMethod() {
    let x = instanceMethod(this.alpha);
  }

  instanceMethod() {
    // Call the super class's implementation
    super.instanceMethod();
  }
}
