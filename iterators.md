# ES 2016 - Iterators

Iterable objects can be used with `for … of`. They contain ordered items.

Access a object's iterator:

```
example[Symbol.iterator]
```

Create an iterator (For an Object)

```
example[Symbol.iterator] = function() {

  let properties - Object.keys(this);
  let count = 0;
  let isDone= false;

  let next = () => {
    if(count >= properties.length) {
      isDone = true;
    }
    return {done: isDone, value: this[properties[count++]]};
  }

  return { next }
}
```

If an object has an iterator it can be used in `for … of` and can be used with
rest and spread. It can also be destructured like an array.
