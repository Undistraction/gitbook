# Strict Mode

Prior to ES6, it was possible to enable _strict mode_ to opt in to a restricted variant of JavaScript. With ES6 it is baked in, so it is unnecessary.

In ES5 it will:

1. Enable errors for things that would have failed silently
2. Improves compiler's ability to optimise by preventing use of some features
3. Prohibits syntax reserved for future use

It is enabled using:

```
'use strict'
```

If you are using a transpiler like Babel, it will transpile your ES6 code down to ES5 and add this declaration automatically.

