# Partial Application

Rather than executing a function with all necessary params, a partially applied function is one that is wrapped in another function which binds one or more params to the wrapped function. This effectively allows one or more of its params to be baked in so it can be called without those params.

```
const calc = (a, b, c) => {
  return (a+b) * c;
}

console.log(calc(1,2,3)); // 9

const paCalc = (a, b) => {
  return (c) => {
    return calc(a,b,c);
  }
}

const alpha = paCalc(10,5);
const beta = paCalc(20, 10);

console.log(alpha(3)); // 45
console.log(beta(2)); // 60
```

The partially applied arguments can be values, but they can also be functions.

