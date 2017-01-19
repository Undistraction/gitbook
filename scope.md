# Scope

JavaScript uses function scope, meaning variables are available anywhere within the same function.  This means most other kinds of block \(for example `if` / `else` blocks\) do not prevent their variables from leaking out.

## Variable Hoisting

JavaScript _hoists_ variables to the top of the current function \(or the document\). This means that variables can be used before they are declared. This means that variables should be declared as early as possible so that they are in the same location that the compiler will ultimately hoist them to.

## this

Note: when using _strict mode_ or in ES6 this is set to undefined when a function isn't called on on object:

```
function alpha() {
  console.log(this);
}

var beta = {
  alpha: alpha
};

console.log(alpha()); // undefined
console.log(beta.alpha()); // Object
```

## Event Handling

When a function is passed to `addEventListener`, it is just that - a function. Even if it was referenced on another object, the object itself isn't passed, so the function loses its context. When running the callback function, it will set `this` to be the target of the event, so whatever function is passed to `addEventListener` will have its `this` set to whatever object is the event target.

```
function Button() {
  this.click = function() {
    console.log(this); // <button id='button'> NOT the instance of Button
  }
}

var button = new Button();

var element = document.getElementById('button');
element.addEventListener('click', button.click);
```

## Call / Apply

Both call and apply do the same thing, but with different syntax. They invoke a function, setting its `this` attribute and passing in  arguments.

```
var alpha = {
  name: 'a'
}

var beta = {
  name: 'b'
}

var charlie = function(prefix) {
  return prefix + this.name;
}

charlie.apply(alpha, ['1']); // 1a
charlie.apply(beta, ['2']); // 2b
```

### Thinking Functionally

In imperative programming we would pass an array to a method which would handle iteration using a for loop, however a functional approach means creating a function that operates on one of the elements at a time. What happens to each item is encapsulated in a function and therefore easily changed.

```
function forEach(list, callback) {
  for (var n= 0; n < list.length; n++) {
    callback.call(list[n], n);
  }
}

var values = [
  { name: 'alpha'},
  { name: 'beta'},
  { name: 'charlie'}
]

var callback = function(index) {
  console.log(index + '/' + this.name);
}

forEach(values, callback);
```

## Arrow Functions

An arrow function isn't supplied with a `this` when it is invoked, but remembers the `this` at the time they were constructed. This means methods defined in a constructor function using an arrow function will always have the context of the constructed instance, even if the method is passed into another function as a callback it will never lose its context.

```
function Button() {
  this.click = () => {
    console.log(">>", this.constructor.name); // Button
  }
}

var button = new Button();
var element = document.getElementById('button');


element.addEventListener('click', button.click);
```

This means that arrow functions used in object literals will have a context of the object itself, but of the current context in which the object is declared.

## Bind

Bind creates a new function with the same body as the function on which it's called, but with its context set to the object passed in to it. This function can then be passed around and called from any context while retaining its own context.

```
function Button() {
  this.click = function() {
    console.log(this); // <button id='button'> NOT the instance of Button
  }
}

var button = new Button();

var element = document.getElementById('button');
element.addEventListener('click', button.click.bind(button);
```



