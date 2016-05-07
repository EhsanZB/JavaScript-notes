## Closures

> 'lexical scoping'

* functions are executed using the `variable scope` that was in effect when they were `'defined'` and NOT the variable scope that is in effect when they are `'invoked'`.
* such `combination of function object and scope` (set of variable bindings in which it was defined), is knows as `'closure'`.

> _scope: The current context of execution._

* In 'lexical scoping', the `scope of a variable` is defined by its `location` within the source code (it is apparent lexically) and `nested functions` have access to variables declared in their `outer scope`.
* the fundamental rule among the 'lexical rules for nested functions' is that, JS functions are executed using the `'scope chain'` that was in effect when it was defined.

> _closures `capture the local variables` of a single function invocation and can use those variables as private state._

* Closures are `functions` that refer to independent (free) variables.
* the function defined in the closure `'remembers' the environment` in which it was created.
* note that according to `'memory management'` issues, we need to `clear the memory` after each time we invoke the closure function.
* because every time we call it, the value of the arguments `reserve in memory` and in the next invocation, the new value for arguments adds to the previous memory.
* to overcome to this issue we assign the `invocation expression` to 'null'.

```js
var fn = doSomething("Hello closure");
fn = null;
```

Example1:

```js
function init() {
    var name = "Mozilla";         // name is a local variable created by init
    function displayName() {      // displayName() is the inner function, a closure
        console.log(name);        // use variable declared in the parent function
    }
    displayName();
}

init(); // Mozilla
```

> _remember that a closure is a `special kind of object` that combines two things: a function, and the environment in which that function was created._

* the environment consists of any `local variables` that were `in-scope` at the time that the closure was created.
* in the example below, `myFunc` has become a closure.
* myFunc is a closure that incorporates both the displayName function and the "Mozilla" string (the local scope variable) that existed when the closure was created.
* Once makeFunc( ) has finished executing, it is reasonable to expect that the name variable will no longer be accessible. BUT it's NOT!
* in the example below, the displayName( ) inner function is returned from the outer function `before being executed`.

```js
function makeFunc() {
    var name = "Mozilla";
    function displayName() {
        console.log(name);
    }
    return displayName;
}

var myFunc = makeFunc();
myFunc(); // Mozilla
```

* in the example below, 'makeAdder' is a 'function factory' —> it creates functions which can add a specific value to their argument.
* 'add5' and 'add10' are both closures.
* actually we create closures (like add5 and add10) in order to `access the variable (private state) outside the inner function` (closure function).
* note that the `nested function has no name`!

```js
function makeAdder(x) {
    return function(y) {        // the closure function
        return x + y;
    };
}

// the closures
var add5 = makeAdder(5);
var add10 = makeAdder(10);

console.log(add5(2));           // 7
console.log(add10(23));         // 33

// equal to:
console.log(makeAdder(5)(2));   // 7
console.log(makeAdder(10)(23)); // 33
```

