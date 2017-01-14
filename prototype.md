# Prototype

Every Object is linked to a Prototype object. It can inherit properties from this object. 

When an attempt is made to retrieve a property that doesn't exist on an object, its prototype object is checked for this property. If it doesn't exist on this object and it too has a prototype object, then that object is also checked. This will continue until either the property is found, or there is no prototype object to check, in which case an exception is raised. This relationship is known as the prototype chain. 

_An object's prototype object is not accessible._

```
var o = {};
o.prototype // undefined
```

The relationship between an object and its prototype is dynamic and ongoing. If properties are added to an object's prototype object, they are immediately available to it. 





