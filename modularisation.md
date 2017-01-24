# Modules

Each file is treated as a separate module. There is no need to wrap the contents in a function to protect them from global scope.

There are two keywords: `import` and `export`.

## Exporting

Variables or functions can be exported using `export`. Anything that isn't exported will not be available outside the module, unless it is exposed by the exported members. When the members to be exported are named, it is a _named export._

```
export const alpha = 'abc';
export function beta() {};
```

It is also possible to export members en-masse at the end of a module.

```
const alpha = 'abc';
function beta() {};

export {alpha, beta}
```

If we have a single member or we want to single out a particular member as the default,  we can use the `default` keyword

```
export default class Alpha {}
```

Using the `default` keyword doesn't prevent us using named exports alongside it. 

```
export default class Alpha {}

export const beta = 'abc';
```

We can rename an export, in which case it will be available only by its new alias. There is no way to rename exports en-masse.

```
export {alpha as beta}
```

## Importing

Variables or functions can be imported using `import`. They are unpacked to the current scope. When exports are named they can be imported using their names.

```
import {alpha, beta} from 'alphabet.js';

alpha // abc
beta // Function
```

We can import all named exports using `*`.

```
import * from 'example.js';
```

To import a default, we use the default keyword, and supply our own name for the imported member:

```
import Example from 'alphabet.js';
```

We can import both default and named exports at the same time:

```
import Example, {beta} from 'alphabet.js';
```

We can also rename a named import:

```
import {beta as charlie} from 'alphabet.js';
```



