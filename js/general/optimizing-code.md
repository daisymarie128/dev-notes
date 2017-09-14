## Optimizing Javascript code

Writing Javascript can make your site more dynamic and active, but the browser's interpretation of this code can introduce inefficiencies and the performace can vary from client to client.

### A few ways to optimize your code are:

#### Define class methods

***Not an ideal way to defin a classes method**
```js
example.Bar = function() {
  // constructor body
  this.foo = function() {
    // method body
  };
}
```

The above code isn't that efficient because each time a instance of `example.Bar` is constructed, a new function and closure is created for `foo`
<br>

A better way of writting this would be to create each seperatly, like so:
```js
example.Bar = function() {
  // constructor body
};

example.Bar.prototype.foo = function() {
  // method body
};
```

Writting it this was means that, everytime an instance of `example.Bar` is created, our `foo` function only ever created once.

### Avoiding pitfalls with closures
Closures are really powerful and useful, however, they have several drawbacks including:<br>
- They are the most common source of memory leaks
- Creating a closure is significantly slower than creating an inner function without a closure, and much slower than reusing a static function. Heres a few examples:

```js
function setupAlertTimeout() {
  var msg = 'Message to alert';
  window.setTimeout(function() { alert(msg); }, 100);
}
```

***This is slower than:***

```js
function setupAlertTimeout() {
  window.setTimeout(function() {
    var msg = 'Message to alert';
    alert(msg);
  }, 100);
}
```
***Which is then slower than:***

```js
function alertMsg() {
  var msg = 'Message to alert';
  alert(msg);
}

function setupAlertTimeout() {
  window.setTimeout(alertMsg, 100);
}
```

Another reason why closures can have draw backs is because they add a level to the scope chain. When the browser resolves properties, each level of the scope chain must be checked. See this example:

```js 
var a = 'a';

function createFunctionWithClosure() {
  var b = 'b';
  return function () {
    var c = 'c';
    a;
    b;
    c;
  };
}

var f = createFunctionWithClosure();
f();
```

So when `f()` is invoked, referencing `a` is slower than referencing `b`, which is then slower than referencing `c`.

### Avoiding browser memory leaks
-  The most common memory leaks for web applications involve circular references between the JavaScript script engine and the browsers' C++ objects' implementing the DOM

One thing to do to prevent browser memory leaks is to use an event system for attaching event listeners.
> The most common circular reference pattern is: [ DOM element --> event handler --> closure scope --> DOM ]
