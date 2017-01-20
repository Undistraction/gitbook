# Array Destructuring

Assigning values from an array to variables.

Before

```
var a = ['alpha', 'beta', 'charlie'];

var alpha = a[0];
var beta = a[1];
var charlie = a[2];
```

After

```
let a = ['alpha', 'beta', 'charlie'];

let [alpha, beta, charlie] = a;
```

Items can be discarded using empty elements:

```
let a = ['alpha', 'beta', 'charlie'];

let [alpha, , charlie] = a;

// alpha = 'alpha'
// charlie = 'charlie'
```

Using rest parameters, multiple array elements can be assigned to a variables

```
let a = ['alpha', 'beta', 'charlie'];

let [alpha, ...rest] = a;

// alpha = 'alpha'
// rest = ['beta', 'charlie']
```

The same is true when assigning the returned value from a function.

