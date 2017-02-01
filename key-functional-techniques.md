# Key Functional Techniques

## Map

Array.prototype.map allows you to iterate over an array and perform an action on each item, returning the result from each iteration. The array returned from the function will be the same length as the array it was called on.

```
const a = [1, 2, 3];
```

## 

## Reduce

Array.prototype.reduce allows you to iterate over an array, passing a function that takes the value returned from the last iteration and the current item and return a single value that will be passed into the next iteration. The function ultimately returns a single value accumulated from all the values.

```
const a = ['A', 'B', 'C'];

const b = a.reduce((x, y) => x + y);

b; // ABC
```



