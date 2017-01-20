# Internals Global vs Function Execution Context

All functions have either a global execution context or function execution context. This is different from a function's context \(accessed through its `this`\). There is a fundamental difference between the two. There is only one global context, but there is a new function context for every invoked function.  Execution contexts are pushed to a FIFO stack.

## Lexical Environment

An execution context provides _identifier resolution _\(the resolution of identifiers to variables\) and does this using the \_lexical environment \_of the function, or the global lexical environment. Each function and block has its own lexical environment \(at least in ES6, before which only functions and try/catch blocks did\). Each environment is able to look through its ancestors when trying to resolve an identifier. If it reaches the global lexical context and still doesn't find anything, this will generate an exception.

This structure is based on function execution, not function location, so that a function's ultimate environment is based on how it was called, not where it was defined. This means that the ancestors of a lexical environment change depending on how it is called.

## Hoisting

The process of moving variables 'to the top' of a function context is often referred to as hoisting. However the actual process of registering identifiers is more complex and differs between block and function/global scope.

### Global Scope

1. Register function declarations \(that are outside of other functions\).
2. Register variables \(`var` that are outside of functions, `let` and `const` that are outside of blocks\).

### Function Scope

1. Create `arguments` object and function parameters.
2. Register function declarations \(that are outside of other functions\)
3. Register variables \(`var` that are outside of functions, `let` and `const` that are outside of blocks\).

### Block Scope

1. Register variables `let` and `const` that are in the current block.



