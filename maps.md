# ES 2016 - Maps

Maps work as key-value stores, similar to objects, but with the crucial
difference that their keys can be objects (object keys are always converted to
keys).

```
let m = new Map();

m.set(alpha. 1);
m.set(beta. 2);

// m.get(alpha) = 1
// m.get(beta) = 2
```

Maps should be used where the keys are unknown at author time. If the keys are
known at author time and are unique strings, then an object can be used.

Maps should only be used if the values are all of the same type.

## Iterating through a Map

```
let m = new Map();

m.set(alpha. 1);
m.set(beta. 2);


for(let [key, value] of m) {}
```

## Weak Maps

Weak maps are a different type of map that only supports objects as keys. No
primitive datatype can be used. The advantage to weak maps is that they have
a weak reference to the key, meaning that if no other object has a reference
to the key, it becomes elegible for garbage collection.
