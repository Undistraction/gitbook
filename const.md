# ES 2016 - Const

Const declares a read-only named constant.

Before
```
var MAX = 99;
```

After
```
const MAX = 99;
```

Constants cannot be redefined in the same scope, but they can be redefined in a
child scope.

Error
```
const MAX = 99;
const MAX = 100;
```

OK
```
const MAX = 99;

function test() {
  const MAX = 44;
}
```

Constants must be assigned an initial value

Error
```
const MAX;
const MAX = 99;
```