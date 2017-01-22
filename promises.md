# ES 2016 - Promises

> A promise is a placeholder for a value that we don't have now but will have later; it's a guarantee that we'll eventually know the result of an asynchronous computation. It will make good on our promise; our result will be a value.

_John Resig, Secrets of the JavaScript Ninja P147_

This value might take the form of an error - a reason for our broken promise.

When a new Promise is constructed, an _executor function_ is passed to it. The executor function has two parameters: `resolve` and `reject`, and is called immediately, being passed in these two built-in functions as arguments. This gives the executor function two ways to deal with a situation depending on whether it is successful or not.

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

To execute a promise, the `then` method is called. Two callback functions are supplied, one for success and one for failure.

```
alphaPromise.then(value => {
    // Succeeded
}, error => {
    // Failed
});
```

## Callback Hell

Promises solve problems inherent with using callbacks. They remove the need to nest callbacks when dealing with a sequence of events and remove the need to check for completion of all parties when dealing with parallel events.

## State

A callback moves through several internal states, depending on the outcome of the situation.

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

If there is an error, we can call reject\(\) from within the promise, which will in turn call the supplied callback function.

```
reject();
```



As well as deliberately calling `reject`  inside a promise.



