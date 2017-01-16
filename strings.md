# Strings

## Escaping Characters

Characters within a string are escaped using the backslash character: \`\\`

```
var example = 'A double quote looks like this: \"';
```

Strings have a length property:

```
var empty = '';
var short = 'abc';
var long = 'abcdefg';

empty.length // 0
short.length // 3
long.length // 7
```

## Mutability

Strings are immutable. They cannot be changed. They are assigned by reference, not value but there is no risk of the references being updated due to their immutability.

```
var x = 'abc';
var a = x;
var b = x;
var c = x;

x = 'xyz';

a // 'abc';
b // 'abc';
c // 'abc';
```

## Comparison

Two strings containing the same characters in the same order are considered to be the same string.

```
var x = 'abc';
var y = 'abc';

x === y // true
```





