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

## Objects

When using objects as arguments, expected keys and values can be provide. Object values are available within the function body through variables named after the keys. Any keys of the params object not supplied will be undefined

Before

```
function test(name="", params={}) {}
```

After

```
function test(name="", {alpha, beta, charlie} = {}) {
  console.log(name); // prints value of alpha
}

test('test', {beta:'test'}); 
```



Default values can also be supplied to the keys of the params object

```
function test(name="", {alpha="1", beta="2", charlie="3"} = {}) {}
```



