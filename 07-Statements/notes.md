## Statements

> Statements are JS sentences or commands and terminated with semicolons (;)

* Note that 'expressions' are evaluated to 'produce a value', but 'statements' are executed to 'make something happen' as listed below.

1. To `evaluate` an expression that has side-effect (such as assignments, function invocations and delete).
   * e.g: 1) greeting = "hello" + name;  2) window.close( ); (the side-effect is affecting the web browser).
   * such expression can be stand-alone as 'statement' and when used like this, they are known as `'expression statement'`.

2. To `declare` an expression that has side-effect (declare new variables and define new functions)
   * such expressions called as `'declaration statement'`.
   * the `'var' and 'function'` are declaration statements.
   * used to define identifiers (variable or function names).
   * in such statements, if a 'var' statement appears `within the body of a function`, it defines `'local variables'` (scoped to that function)
   * and when used in the 'top-level code', it defines `'global variable'`.
   * if no initializer is specified, then the initial value for the variable is `'undefined'`.

3. To `alter the default` order of execution (by using 'control structures' statements).

> Control structure:

* JS interpreter executes the statements one after another `in the order they are written`.
* using control structure's statements we can `alter` such default order.

1. `conditionals` : if/switch,... (make interpreter to execute or skip the statements depending on the value of the expression)
2. `loops` : for/while,... (executing the statements repetitively)
3. `jumps` : break/return/throw,... (jump to another part of the program)

> Statement block:

* it's a `sequence of statements` enclosed within curly braces.
* combines multiple statements into a single 'compound statement.
* e.g: the while loop syntax includes a single statement that serves as a body of the loop. using statement block, we can place any number of statements within this single allowed sub-statement.
* `compound statements` allow us to use multiple statements where JS expects a single statement.

> Empty statement:

* is opposite of the compound statements.
* it allows us to `include no statement` while JS expects one statement (applying ;).
* one of the useful usage of empty statements is when we want to create a loop that has an empty body.

```js
// initializing the elements of 'elm' to zero (note that this statement has no {})
for (var i=0;i<elm.length;elm[i++]=0)    /* empty */;
```

> Defining a function using `'function expression'` --> is a `function literal`.

```js
var square = function(x){return x * x;}; // assigning the function to a variable.
```

> defining a function using `'function statement'` --> function `declaration` statement.

* the statements inside the body of the function are not executed when the function is defined.
* the statements inside the curly braces are `associated with the new function object` for execution when the function is invoked.
* function statement may appear in `top-level code` or may be `nested` within other functions.
* if nested then only appears `locally`, in top-level of the function that is nested within.

```js
function square(x){return x * x};      // the statement includes the variable name (as an identifier).
```

> _Difference between the functions that are created by statement and expression?_

* note that both forms create a new function object.
* in function statement, the function name is included, but in expression declaration, function name appears as a variable and the function object has been assigned to it.
* the functions that are defined by `function declaration are implicitly 'hoisted' to the top` of the containing script or function.
* so that all functions in a script or all nested functions in a function are declared before any other code run.
* so we can `invoke (call) a function before you declare it`.

> Hoisting:

* hoist means to pull up something
* Because variable declarations (and declarations in general) `are processed before any code is executed`, declaring a variable anywhere in the code is `equivalent to declaring it at the top`.
* Hoisting is JavaScript's `default behavior` of moving all declarations to the top of the `current scope` (to the top of the current script or the current function).
* variable `declaration is moved to the top` of the function or global code.
* in JS a variable can be declared 'after' it has been used.
* it means that, a `variable can be used 'before' it has been declared`.

```js
num = 5;
console.log(num);
var num;
```

* note that `JavaScript only hoists declarations`, not initializations.
* to avoid bugs, always declare all variables at the beginning of every scope.

```js
// example#1
var x = 5;
var y = 7;
console.log( x + " , " + y); // 5 , 7
```

```js
// example#2
var x = 5;
console.log( x + " , " + y); // 5 , undefined
var y = 7;
```

> 'declared' vs 'undeclared' variables:
