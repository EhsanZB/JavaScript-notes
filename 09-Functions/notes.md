## Functions

* functions are `values` in JS. the 'typeof' operator returns the string 'function' when applied to a function.
* BUT functions are really a special kind of JS object -> since functions are objects so they can `have properties and methods`.
* in JS, functions are object -> so it's possible to set properties on them or even invoke methods on them.
* there is even a `functions constructor` to create new function object.

> _just to remind that everything in an object is `property` (with key/name and value), but if the value of a property is a function, then that property is `considered as method` of that function._

* Function instances inherit methods and properties from `Function.prototype`.

> _note that function invocation (calling a function) provides values or 'arguments' for function's 'parameters'._

* function uses its arguments to `calculate` a value or expression to `return`.
* `'this' keyword` --> each invocation has invocation context that is the value of 'this'.
* if a function is assigned to the property of an object, it's known as 'method' of that object.

> _when a function is invoked `on or through an object`, that object is invocation context `'this'` value of the function._

> functions can be nested within another functions --> they have access to any variables that are in 'scope' where they are defined.

* it means that JS `functions are 'closures'`.

```js
// function definition 'expression'
var functionName = function (x){
    return x+1;
};

// function declaration 'statement'
function functionName (x){
    return x+1;
}
```

Examples:

```js
// example1
function addStatement(x,y){
    return x+y;
}
console.log(addStatement(2,3));

// example2
var addExpression = function(x,y){
    return x+y;
};
console.log(addExpression(2,3));
```

* note that function declaration statements are 'hoisted' to the top of the enclosing script (or enclosing function).

> _if a function expression includes a name, the local scope for that function will include a binding of that name to the function object. function name becomes a local variable within a function._

* note that we cann't refer to a function defined as an expression `until it's assigned to a variable`!
* so functions defined with expressions can not be invoked before they are defined (no hoisting!).

Another difference between functions defined with expression or statement is that:

* function declaration with `statements` can appear in global code or within other functions (JS allows such functions as top-level statement).
* BUT not inside a loop, try/catch, conditionals.
* function declaration with `expression` can appear `anywhere in the code`.

> _function is not executed when defined._

* there are 4 ways in JS to invoke a function:

1. as `functions` (function invocation),
2. as `methods` (method invocation),
3. as `constructors` (constructor invocation),
4. and `indirect call` using apply() and call()

#### 1. function invocation

* the return value of the function becomes the `value of the invocation expression`.
* note that in strict mode, the context invocation `(this) is undefined` in such regular function invocations.

#### 2. method invocation

* method invocation is just calling a function which is a value of a property name in an object.
* invocation using 'dot' notation --> 'property access'
* also note that the object becomes the invocation context ('this' keyword).

```js
var calculate = {
    val1 : 10,
    val2 : 32,
    add : function(){
        return this.val1 + this.val2;
    },
    minus : function(a,b){
        return a-b;
    }

};

// invocation using property access
console.log(calculate.add());         // 42

// invocation using []
console.log(calculate["minus"](5,2)); // 3
```

> More about 'this' keyword:

* 'this' is just a keyword `not a variable or property name`! (JS does not allow us to assign a value to 'this').
* (unlike variables) 'this' doesn't have scope and also the `nested functions do not inherited the 'this'` value of the containing function.
* if a nested function is invoked as a `method` --> its 'this' value is the 'object' it was invoked on.
* if a nested function is invoked as a `function` --> its 'this' value will be either the 'global object' in non-strict mode and 'undefined' in `strict mode`.

> _it is very important to note that a nested function can NOT use 'this' value to obtain the invocation context of the outer function._

* so to access the 'this' value of the outer function --> we need to store that value into a variable that is in scope for the inner function (it's common to use 'self' variable name for such storing).

```js
var o = {

  myMethod : function () {
      var self = this;
      console.log(this === o);       // true
      nestedFunction();              // invoked as a function

      function nestedFunction(){
          console.log(this === o);   // false
          console.log(self === o);   // true
      }
  }

};

o.myMethod(); // invoking myMethod on the object o (invoked as a method)
```

#### 3. constructor invocation

* if a function or method invocation is preceded by `'new' keyword`, then it is a constructor function (as an initializer).
* remember that in JS we have 4 `built-in constructors` which serve to initialize a newly created object (Object,Array,Date,RegExp).
* it's common to `define our own constructor functions` to initialize the newly created object.
* when the function has argument(s) then such argument expressions are evaluated and passed to the function (same way as function and method invocations).
* note that if the constructor function has `no argument`, then the () can be `omitted`.

```js
// same expressions
var obj1 = new Object();
var obj2 = new Object;
```

* a constructor invocation `creates a new (and empty) object` that 'inherits' from the `'prototype' property` of the constructor.
* it means that the 'prototype property' of the constructor function is used as a prototype of the newly created object.
* note that all objects `inherit a constructor property` from their prototype.

```js
var a = [];
console.log(a.constructor === Array);  // true

var n = new Number(3);
console.log(n.constructor === Number); // true
```

> _The newly created object is used as the 'invocation context'._

* so a constructor function can refer to that context using 'this'.
* note that the new object is used as the invocation context, even if it looks like a method invocation.
* for example in `'new o.myMethod( )'`, o is not used as the invocation context.

> _The new object is the value of the constructor invocation expression._

* constructor functions `do not use 'return'`, they typically `'initialize'` the new object and return implicitly when they reach the end of their body.
* if constructor use return to return an object --> then that object becomes the `value of the invocation expression`.

> _The constructor initializes the object and can provide access to its private information._

* a constructor in JavaScript is usually declared at the `instance of a class`.

#### 4. indirect invocation

* JS functions are objects so like all other JS objects, they have methods. (such as apply() and call()).
* `call() and apply()` both used to invoke the function `indirectly`.
* the `first argument` for both call and apply is the `object` on which the function is to be invoked (and becomes the value of 'this').
* the difference is that in `apply( )` we passing arguments are in `array format`.
* apply( ) works with array-like objects as well as true arrays.

```js
// finding the largest number in an array on numbers
var biggest = Math.max.apply(Math,[23,55,27,275]);
console.log(biggest); // 275
```

* note that except the first argument in call or apply, `the rest arguments` are the values that are passed to the function.
* if we want to use a method of an object for another object, then we can indirectly invoke the method through the original object.

```js
var bar = {
    name : 'First Object',
    doSomething : function(x,y){
        return this.name + ': ' + x + ',' + y;

    }
};

var foo = {
    name : 'Second Object'
};


console.log(bar.doSomething(1,2));             // First Object: 1,2
console.log(bar.doSomething.call(foo,1,2));    // Second Object: 1,2
console.log(bar.doSomething.apply(foo,[1,2])); // Second Object: 1,2
```



