# Key Functional Techniques

## Reduce

Array.prototype.reduce allows you to iterate over an array, passing a function that takes the value returned from the last iteration and the current item and return a single value that will be passed into the next iteration.

```
const a = ['A', 'B', 'C'];

const b = a.reduce((x, y) => x + y);

b; // ABC
```



