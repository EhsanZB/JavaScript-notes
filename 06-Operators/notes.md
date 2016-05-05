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

