# ES 2016 - Object Initialising and Destructuring

When initializing an object where its keys are the same as existing variables or
params:

Before
```
function example(alpha, beta) {
  let charlie = 'charlie';
  return {alpha: alpha, beta: beta, charlie: charlie};
}
```

After
```
function example(alpha, beta) {
  let charlie = 'charlie';
  return {alpha, beta, charlie};
}
```

Functions added to an object can also be simplified

Before
```
let example = {
  example: function(){}
}
```

After
```
let example = {
  example(){}
}
```

Similarly, objects can be destructured to variables (All or some properties can
be destuctured).

Before
````
let example = {alpha: 1, beta: 2, charlie: 3};

var alpha = example.alpha;
var beta = example.beta;
var charlie = example.charlie;
```

After
```
let example = {alpha: 1, beta: 2, charlie: 3};

let { alpha, beta, charlie } = example;
```
