# ES2016 - Modules

## Importing and Exporting

Before

```
<!DOCTYPE html>
<body>
  <script src="./jquery.js"></script>
</body>

<!-- Then access using global variables, e.g. let x = $('.example'); -->
```

### Default Export

Using `export default` allows a single export per module. When imported, the  
export is assigned a local name.

```
<!DOCTYPE html>
<body>
  <script src="./example.js"></script>
  <script src="./app.js"></script>
</body>

// example.js
export default function() {}

// app.js
import alpha from '/example.js';

alpha();
```

### Named Exports

Using named exports allows multiple exports from a single module.

```
<!DOCTYPE html>
<body>
  <script src="./example.js"></script>
  <script src="./app.js"></script>
</body>

// example.js
export function alpha(){}
export function beta(){}

// app.js
import alpha from '/example.js';
import beta from '/example.js';

alpha();
beta();
```

### Import As Object

```
<!DOCTYPE html>
<body>
  <script src="./example.js"></script>
  <script src="./app.js"></script>
</body>

// example.js
export function alpha(){}
export function beta(){}

// app.js
import * as example from './example.js';

example.alpha();
example.beta();
```

### Single export declaration

```
// example.js
function alpha(){}
function beta(){}

export {alpha, beta}
```

### Single import declaration

import {alpha, beta} from './example.js'

## Constants

Export and import of constants is identical to functions.

```
// constants.js
const ALPHA = 'alpha';
const BETA = 'beta';

export {ALPHA, BETA};

// app.js
import {ALPHA, BETA} from 'constants.js';
```

## Classes

Default export

    // clazz.js
    export default class Example {}

    // app.js
    import Example from `./example.js`;
    new Example();

Named export

    // clazz.js
    class Example {}

    export { Example }

    // app.js
    import { Example } from `./example.js`;
    new Example();



