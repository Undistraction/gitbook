# Callbacks

A callback is a function that is stored for execution at a later point. 

```
var callbackFunction = function() {
    console.log('Called back');
}

function doSomething(callback) {
    console.log('Doing something');
    callback();
}

doSomething(callbackFunction); // Doing something | Called back
```



