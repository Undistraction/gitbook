# ES 2016 - Variadic Functions

A variadic function is a function that takes a varying number of parameters. In
ES2016, rest parameters make this possible.

```
function test(...params) {}
```

Rest params must always be the last parameter of a function

Error
```
function test(...params, alpha);
```

Rest params do not automatically destructure arrays to parameters. The spread
operator is needed for this:

```
function test(...params) {}

var a = [1,2,3,4];

test(...a);
```