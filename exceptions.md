# Exceptions

Exceptions are created using `throw` and passing in an object containing a `name` and `message`.

```
throw {
    name: 'Alpha',
    description: 'An alpha exception'
};
```

To handle exceptions, a `try`/`catch` clause should be used, with the exception object being passed into the `catch` clause.

```
try {
    alpha();
} catch (exception) {
    // Handle exception
}
```



