# Property Descriptors

Each property of an object is described by a _property descriptor_.This object contains information about the property:

* **configurable **\(Boolean\) Can the property value be changed or deleted?
* **enumerable **\(Boolean\) Can the property value be enumerated in a `for`/`in` loop.
* **value **\(\*\) The value of the property \(`undefined` by default\).
* **writable **\(Boolean\) Can the property value be changed using assignment?
* **get **\(Function\) The _getter _function used to access the property.
* **set **\(Function\) The _setter_ function used to access the property.

The descriptor of a property can be accessed using `Object.getOwnPropertyDescriptor`. When a property is created using assignment, it will be `configurable`, `enumerable` and `writable`, and its `value` will be set.

```
var alpha = {
        beta: 'abc'
    }
    
Object.getOwnPropertyDescriptor(alpha, 'beta'))

// [object Object] {
//    configurable: true,
//    enumerable: true,
//    value: "abc",
//    writable: true
// }
```

When we want control over the descriptors we use Object.defineProperty:

```
Object.defineProperty(alpha, 'charlie', {
    configurable: false,
    enumerable: false,
    value: true,
    writable: true
    });
```



