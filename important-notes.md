# Important Notes

## Referencing Functions

Whenever a function is stored in a variable, it is stored as an independent function. If it doesn't have its context stored within it \(because it is bound or was created using an arrow function\), it loses any context. it doesn't matter how many objects have been traversed in referencing it, it will no longer have that context. 

Effectively, when referenced again from the variable the following two contexts will be identical \(note this does not apply to closure\): 

```
var alpha = beta.charlie.delta;
var alpha = delta
```

## Closures vs Context

Although they are related, closures and context are not the same thing. The things a function has access to are defined by both. A function called in two different contexts will retain access to anything it closed over, but other references, including references to properties on `this`, might refer to completely different things.





