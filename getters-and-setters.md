# Getters and Setters

Getters and setters are defined using the `get` and `set` keywords. They are functions that are accessed as if they were properties. They can be used on objects or class definitions. They can be used individually or separately. The variable must not be named identically to the getter and setter. 

```
var alpha = {
  
  _name: 'abc',
  get name() {
    return this._name;
  },
  set name(value) {
    this._name = value;
  }
}

alpha.name // abc
alpha.name = 'def';
alpha.name // def
```

The problem with this approach is that the property is still accessible from outside the object. 

```
alpha._name // abc
```

By using `Object.defineProperty` alongside closure, a private variable can be created.

_Note: The property name has an underscore, but is without an underscore when passed into `Object.defineProperty`._

```
var Alpha = function(){
  
  var _name =  'abc';
      
  Object.defineProperty(this,
    'name', 
    {
      get: () => {
        return _name;
      },
      set: (value) => {
        _name = value;
      }
    }
  )    
}

var alpha = new Alpha();

console.log(alpha.name)
alpha.name = 'def';
console.log(alpha.name)
```



