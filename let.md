# ES 2016 - Let

Normally variables are hoisted to the top of the containing function block when
the JS is compiled. By using `let()` to define a variable it is not hoisted,
existing only in the place it is declared.

Before
```
var x = 22;
```

After
```
let x = 22;
```

Let can be used in a for loop to ensure a separate version of i is available in
each iteration.

Before
```
for(var i = 0; i < 10; i++) {}
```

After
```
for(let i = 0; i < 10; i++) {}
```

You cannot redefine a variable declared using let in the same block, but a new
variable can be defined that shadows a variable of the same name in a parent
block:

Error
```
let x = 10;
let x = 11;
```

OK
```
let x = 10;

function test() {
  let x = 11;
}
```
