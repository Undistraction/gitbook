# ES 2016 - Promises

Useful Resources;

1. [http://www.mattgreer.org/articles/promises-in-wicked-detail/](http://www.mattgreer.org/articles/promises-in-wicked-detail)
2. [http://exploringjs.com/es6/ch\_promises.html](http://exploringjs.com/es6/ch_promises.html)
3. Codepen: [https://jsbin.com/kabamufoju/9/edit?html,js](https://jsbin.com/kabamufoju/9/edit?html,js)

> A promise is a placeholder for a value that we don't have now but will have later; it's a guarantee that we'll eventually know the result of an asynchronous computation. It will make good on our promise; our result will be a value.

_John Resig, Secrets of the JavaScript Ninja P147_

This value might take the form of an error - a reason for our broken promise.

## Important Fundamentals

1. The execution function passed to a Promise is called immediately
2. `then` always returns a new Promise.
3. A promise has an internal `PromiseValue` property.
4. A promise has an internal `PromiseStatus` property that tracks its state \(either `pending` or `resolved`\).
5. The value passed in to a resolved handler is the outcome of the previous promise's execution function
6. A function that returns a promise is a _promise-based-function_. Resolution callbacks are often promise-based-functions, returning a Promise.

## Callback Hell

Promises solve problems inherent with using callbacks. They remove the need to nest callbacks when dealing with a sequence of events and remove the need to check for completion of all parties when dealing with parallel events.

## Creation

When a new Promise is constructed, an _executor function_ is passed to it. The executor function is responsible for doing whatever the Promise needs to do. The executor function has two parameters: `resolve` and `reject`, and is called _immediately_ by the promise, being passed in these two built-in functions as arguments. This gives the executor function two ways to deal with a situation depending on whether it is successful or not. Although the executor function has access to the promise's resolve and reject methods, the promise doesn't have access to callbacks for these eventualities as these haven't been supplied yet.

To create a promise:

```
const alphaPromise = new Promise((resolve, reject) => {
    if(Math.random() > 0.5) {
        resolve('Success');
    } else {
        reject('Failure');
    }
})
```

It is also possible to create a promise that is already resolved using:

```
Promise.resolve(value);
```

## Then

To pass callbacks into a Promise,  the `then` method is called. Two callback functions can be supplied, one for success and one for failure. A new promise is always returned.

```
alphaPromise.then(value => {
    // Succeeded
}, error => {
    // Failed
});
```

If `then` is called on a promise which is not resolved, the promise waits for resolution before triggering the callback.

The value that a promise resolves is passed into this handler, and the value returned from this handler is passed into the following promise's resolve.

## Calling _then Multiple Times_

If `then` is called on a promise multiple times before it is fulfilled, each callback is stored and all will be executed when it becomes fulfilled, in the order they were added.

```
var alphaMethod = function(value) {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve(++value), 4000);
  });
}

var p1 = alphaMethod(1);

p1.then((value) => console.log('A', value));
p1.then((value) => console.log('B', value));
p1.then((value) => console.log('C', value));

// A2
// B2
// C2
```

Once a callback has been _fulfilled_, subsequent calls to `then` will result in the callback supplied to `then` being called immediately.

```
var alphaMethod = function(value) {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve(++value), 4000);
  });
}

var p1 = alphaMethod(1);

p1.then((value) => {
  console.log('A', value);
  afterResolved(value);
});

function afterResolved(value) {
  p1.then((value) => console.log('B', value));
  p1.then((value) => console.log('C', value));
}

// A2
// B2
// C2
```

## State

A callback contains state and moves through two internal states, depending on the outcome of the situation.

1. **Pending **This is its default state. 
2. **Fulfilled **This is the state when the Promise has been successfully fulfilled.
3. **Rejected **This is the state when the Promise has errored.

While a promise is pending it is known as an _unresolved_ promise. When it is fulfilled or rejected it is _resolved._ A Promise cannot move from fulfilled to rejected or vice-versa.

## Fulfilment

If a promise is fulfilled, we can call resolve\(\) from within the promise, which will in turn call the supplied callback function.

```
resolve();
```

## **Rejection**

If there is an error, we can call `reject()` from within the promise, which will in turn call the supplied callback function. If an exception occurs and we don't call `reject` ourselves, it will be called automatically.

```
reject();
```

As well as deliberately calling `reject`  inside a promise, there is another way to handle errors. Instead of passing in a second callback, a `catch` method can be chained to the `then` method.

```
alphaPromise.then(() => // Success handling).catch(error => // Error Handling);
```

## Basic Promise

Inside a promise we will usually be performing some kind of asynchronous operation which will either succeed \(in which case be call resolve and pass any necessary data or messages to it\) or fail \(in which case we call reject and pass an error message. In case the operation itself causes an exception we might want to wrap the operation itself in a`try`/`catch` block. Although an exception will cause `reject` to be called automatically, by catching any exception, we can control what information is passed to `reject`.

## Chaining Promises

To understand chaining, it is crucial to understand the `then` method.

> If you return a value, the next `then()`is called with that value. However, if you return something promise-like, the next  `then()` waits on it, and is only called when that promise settles \(succeeds/fails\).

_Google Developer Promises Docs_

Because a call to then returns another promise, we can chain multiple promises together:

```
methodThatReturnsPromise(alpha)
    .then(value => methodThatReturnsPromise(beta))
    .then(value => methodThatReturnsPromise(charlie))
```

Error Handling can be done inline with a separate `catch` for each Promise:

```
methodThatReturnsPromise(alpha)
    .then(value => methodThatReturnsPromise(beta))
    .catch((error) => // Error handling)
    .then(value => methodThatReturnsPromise(charlie))
    .catch((error) => // Error handling)
    .then(value => methodThatReturnsPromise(delta))
    .catch((error) => // Error handling)
```

Or it can be done for all Promises with a single `catch`:

```
methodThatReturnsPromise(alpha)
    .then(value => methodThatReturnsPromise(beta))
    .then(value => methodThatReturnsPromise(charlie))
    .then(value => methodThatReturnsPromise(delta))
    .catch((error) => // Error handling)
```

## Parallel Promises

Promises can be used in parallel instead of sequence.

### Wait for All

```
Promise.all([methodThatReturnsAPromise(alpha),
    methodThatReturnsAPromise(beta),
    methodThatReturnsAPromise(charlie),
    methodThatReturnsAPromise(delta)])
    .then(results => // Handle results)
    .catch((error) => // Error handling)
```

### Wait for First

```
Promise.race([methodThatReturnsAPromise(alpha),
    methodThatReturnsAPromise(beta),
    methodThatReturnsAPromise(charlie),
    methodThatReturnsAPromise(delta)])
    .then(results => // Handle results)
    .catch((error) => // Error handling)
```



