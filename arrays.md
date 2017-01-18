# ES 2016 - Array

## Iterating

Iterating through the objects in an array is now much simpler

Before
```
var a = ['alpha', 'beta', 'charlie'];

for(let i in a) {
  // a[i]
}
```

After
```
let a = ['alpha', 'beta', 'charlie'];

for(let v of a) {
  // v
}
```

## Searching

Arrays now include a `find` method. By passing a function to this method, the
item is passed to the function, and will be found if it returns true.

```
let a = ['alpha', 'beta', 'charlie'];

let result = a.find( (v) => {
    return v.length > 4;
})

// a = 'alpha'
```

Similarly, multiple items can be found using `filter`

```
let a = ['alpha', 'beta', 'charlie'];

let result = a.filter( (v) => {
    return v.length > 4;
})

// a = ['alpha', 'charlie']
```

Either of these can be shortened using:

```
let result = a.filter( v => v.length > 4);
```
