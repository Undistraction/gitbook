# ES 2016 - Function Defaults

Functions now support default parameters:

```
function test(value=[]) {

}
```

When using objects as arguments, it is now possible to name the keys, making
the function signature much more readable. This also results in the keys being
made available within the function as variables

Before
```
function test(name="", params={}) {}
```

After
```
function test(name="", {alpha, beta, charlie} = {}) {
  console.log(alpha); // prints value of alpha
}
```

Any keys of the params object not supplied will be
undefined

```
test('test', {beta:'test'});
```

Default values can also be supplied to the keys of the params object

```
function test(name="", {alpha="1", beta="2", charlie="3"} = {}) {}
```
