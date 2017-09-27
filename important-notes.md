# Closure

## Closures vs Context

Although they are related, closures and context are not the same thing. The things a function has access to are defined by both. A function called in two different contexts will retain access to anything it closed over, but other references, including references to properties on `this`, might refer to completely different things.

