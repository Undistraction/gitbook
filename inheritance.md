# Inheritance

Inheritance provides two advantages:

1. Allows code to be reused, so that only the differences need to be specifies instead of all the similarities repeated.
2. Allows specification of Types

**Prototype Objects**

1. All objects have a `constructor` attribute that they have inherited through the prototype chain from Object.prototype.constructor.

2. All objects have a \_\_proto\_\_ attribute.

This means that any object can replace a Function's `prototype` attribute.

By setting a constructor's prototype attribute to the instance of an object,  the attributes of that object become available to any object instances constructed from it. 



