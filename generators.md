# ES 2016 - Generators and Iterators

A generator is a special kind of function that can return multiple values. They are asynchronous in so far as they are able to pause between returning values.

Define a generator:

```
function* AlphaGenerator() {}
```

They return values using the `yield` keyword.

```
function* AlphaGenerator() {
    yield 1;
    yield 2;
    yield 3;
}
```

They are accessed through an _iterator_ object, returned by executing the function.

```
function* AlphaGenerator() {
    yield 1;
    yield 2;
    yield 3;
}

const alphaIterator = AlphaGenerator();
```

Every call to the iterator's next\(\) method will return an object with two properties: `value` and `done`. If there is a value to return the object will contain the value in the `value` property and `done` will be set to `false`.

```
{
    value: 1,
    done: false
}
```

If there are no more values to return, `value` will be `undefined` and `done` will be `false`.

```
{
    value: undefined,
    done: false
}
```

Note: Each iterator starts fresh and will iterate independently of any others without effecting them.

## For / Of Loops

Iteration can be performed using a `for`/`of` loop, in which case the value is mapped to the loop's variable.

```
for(let value of AlphaIterator()) {
  value // 1, 2, 3
}
```

## Yielding To Another Generator

A generator can yield to another generator, in which case all the values of the yielded generator will be yielded in place of this yield:

```
function* AlphaGenerator() {
    yield 1;
    yield* BetaGenerator();
    yield 4;
}

function* BetaGenerator() {
    yield 2;
    yield 3;
}

for(let value of AlphaIterator()) {
    value // 1, 2, 3, 4
}
```

## Endless Generator

A generator doesn't have to have a finite number of values, for example it can be used to generate an ever increasing series of numbers:

```
function* AlphaGenerator() {
    let i = 0;
    while(true) {
        yield i++;
    }
}
```

## Passing Data To An Iterator

Value\(s\) passed in to a call to an iterator function will be available inside that function:

```
function* AlphaGenerator(value) {
    yield 1 + value;
    yield 2 + value;
    yield 3 + value;
}

for(let value of AlphaGenerator('A')) {
    value // A1, A2, A3
}
```

Values passed in to a call to next\(\) will be the return value of the previous yield:

```
function* AlphaGenerator(value1) {
    let value2 = yield (1 + value1);
    let value3 = yield (2 + value2);
    yield 3 + value3;
}

var letters = ['A', 'B', 'C'];

var iterator = AlphaGenerator(letters[0]);

for(var i = 0; i < 3; i++) {
    console.log(iterator.next(letters[i]).value)
}
```



