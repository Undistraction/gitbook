# ES 2016 - Template Strings

Template strings are declared using backticks.

Before
```
let alphs = 'alpha';
let beta = 'beta';

let charlie = alpha + ' ' + beta;
```

After
```
let alphs = 'alpha';
let beta = 'beta';

let charlie = `${alpha} ${beta}`;
```

Backticks can also be used to wrap multiline text

```
let alpha = `beta

charlie
delta

echo`
```
