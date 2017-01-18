# ES 2016 - Object Assign

Object assigning allows objects to be merged into a single object. It is a
variadic function and will take multiple objects, with the first object being
mutated. If two objects contain the same key, the key of the object that appears
later in the parameter list will be used.

```
let a = {
  alpha: 'A',
  beta: "A",
  charlie: "A"
};

let b = {
  beta: "B",
  charlie: "B"
};

let c = {
  charlie: "C"
};

let d = Object.assign({}, a,b,c);

// d = {
//   alpha: "A",
//   beta: "B",
//   charlie: "C"
//}
```