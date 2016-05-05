## Operators

* Operators are used for the tasks below in JS:

1. `Arithmetic` expression +,-,*,....
2. `Comparison` expression >,>=,in,instanceof,...
3. `Logical`    expression &&,||
4. `Assignment` expression =
5. `Relational` expression ==,===,!=,!==
6. `Evaluation` expression eval("2+3") --> 5

> Operators with `higher precedence` are performed before those with lower precedence. For example * has higher precedence than + so: var num = 2+3*5 = 17  (3x5=15 then 2+15)

* Operator precedence `can be overridden` by using ( ): var num = (2+5)*5 = 50

> `unary` operators: have only 1 operand

* (e.g: ++,+,-,!,type of,~,....)  (+/- are also located in binary operators)

> `binary` operators : have 2 operands

* (e.g: <, >=,in,==,===,&,&&,....) (== loose equality, === strict equality)

> `ternary` operators : have 3 operators

* (e.g: '?:') x > 0 ? x : -x (conditional operator)

```js
console.log(5+2);           // 7
console.log(5+2+"Ehsan");   // 7Ehsan
console.log(5+(2+"Ehsan")); // 52Ehsan
console.log("5"+"2");       // 52 (typeOf is string, not number)
console.log(5*2);           // 10
console.log(5/2);           // 2.5

// '%' called as 'Modulo'
console.log(5%2);           // 1 (reminder of 5/2, using whole-number in division process!) --> 2x2=4, 5-4=1

// finding even numbers (0,2,4,6,8,10)
for ( var i=0; i<=10; i++ ){
    if ( i%2 == 0 ){
        console.log(i);
    }
}
```

> Increment (++): increments (adds one to) its operand and returns a value. There are 2 types of increment:

1. `postfix` (post-increment) a++  (it returns the value `'before'` incrementing)
2. `prefix`  (pre-increment) ++a   (it returns the value `'after'` incrementing)

```js
var a = 3;
post = a++;        // 3

console.log(a);    // 4
console.log(post); // 3


var b = 3;
pre = ++b;        // 4

console.log(b);   // 4
console.log(pre); // 4
```

#### Property existence:

example:

```js
var p = {x:1, y:1};
console.log("x" in p);        // true
//console.log(x in p);        // ERROR! (x in not defined)
console.log("toString" in p); // true (p inherits toString)

var a = [7,8,9];
console.log("0" in a);    // true (a has an element "0") index 0
console.log("1" in a);    // true (a has an element "1") index 1
console.log("2" in a);    // true (a has an element "2") index 2
console.log("3" in a);    // fasle

console.log(0 in a);      // true (a has an element "0") index 0   // numbers are converted
console.log(1 in a);      // true (a has an element "1") index 1
console.log(2 in a);      // true (a has an element "2") index 2
console.log(3 in a);      // false

console.log(7 in a);      // false
console.log("7" in a);    // false
```

#### Object type (instanceof):

example:

```js
var date = new Date();
console.log(date instanceof Date);   // true
console.log(date instanceof Object); // true
console.log(date instanceof Number); // false

var num = 57;
console.log(num instanceof Object);  // false
console.log(num instanceof Number);  // false

var num = Number(57);
console.log(num instanceof Object);  // false
console.log(num instanceof Number);  // false

var num = new Number(57);
console.log(num instanceof Object);  // true
console.log(num instanceof Number);  // true
```