# Default Parameters

Functions now support default parameters:

```
function test(value=[]) {
```

Parameters have access to previous parameters:

```
function test(alpha='a', beta='b', charlie=alpha+beta) {
  charlie // 'ab'
}()
```

## 

## Objects

When using objects as arguments, it is possible to provide the names of the expected keys, making the function signature much more readable. This also results in the keys being made available within the function as variables

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



