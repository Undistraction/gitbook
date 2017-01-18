# ES 2016 - Promises

Promises prevent async code from blocking.

Before
```
let results = getFromServer();

// Subsequent code only run once getFromServer() returns a value
if (results) {
  handleSuccess();
} else {
  // Handle error
}
```

Continuation Passing Style (CPS) is better, but can result in nested callbacks.
```
getFromServer( function(results) {
  // Code runs once getFromServer() returns a value
  if (results) {
    handleSuccess();
  } else {
    // Handle error
  }
});
// Subsequent code runs instantly
```

After
```
// Construct Promise
function getFromServer() {
  return new Promise(function(resolve, reject) {
    // Make request
    // If successful
    resolve(results);
    // if unsuccessful
    reject()
  });
}

// Envolk the promise
getFromServer() {
  .then(handleSuccess)
  .catch(function(error) {
    // Handle error
  });
}
```

An active promise moves through a pending state to either rejection or
resolution.
