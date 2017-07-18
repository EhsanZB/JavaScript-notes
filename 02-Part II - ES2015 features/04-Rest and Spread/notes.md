## Rest and Spread Operators

> Such operators are used in situations that we need to accept ANY NUMBER of argument.

#### The de-structuring assignment

* is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables. (`Source: MDN-mozilla`)

```js
//example1
[a, b, ...rest] = [10, 20, 30, 40, 50];

console.log(a); // 10
console.log(b); // 20
console.log(rest); // [30, 40, 50]

//example2
var x = [1, 2, 3, 4, 5];
var [y, z] = x;

console.log(y); // 1
console.log(z); // 2

//example3
// Array de-structuring
var foo = ['one', 'two', 'three'];
var [one, two, three] = foo;

console.log(one); // "one"
console.log(two); // "two"
console.log(three); // "three"

//example4
var a, b;
[a=5, b=7] = [1];

console.log(a); // 1
console.log(b); // 7

//example5
var a = 1;
var b = 3;
[a, b] = [b, a];

console.log(a); // 3
console.log(b); // 1

//example6
function f() {
  return [1, 2];
}

var a, b;
[a, b] = f();

console.log(a); // 1
console.log(b); // 2
```

#### Rest Operator

* it allows us to represent an indefinite number of arguments as an array.
* For example, if our passed arguments are (1,2,3) then `...numbers` is equal to [1,2,3].
* in the example below, we accept all arguments and `encapsulate` them in an `array` `numbers` (think of it as the Rest of the numbers!).
* note that in this example, if we omit the `...` then `numbers` will refer to the `first passed argument` which is `1` in this case!

```js
function sum(...numbers) {

	// reduce down the array values into a single value
	 return numbers.reduce((prev, current) => {
		return prev + current;
	 })


	// way #2 (OLD)
	let total = 0;
	numbers.map(number => {
		total = total + number;
	});

	return total;
}

console.log(sum (1,2,3));
```

> in case that we have more than one arguments (except the REST), make sure that the `REST` operator (argument) is located at the `END OF THE argument list`.

* In this example:
    * `foo` refers to `1` and `...numbers` refers to the rest of the arguments: `2`,`3`,`value`
    * DO NOT MOVE `...numbers` (REST operator) to the fist argument! (try to play with passed arguments to this functions)
    * so here `value` doesn't necessary refer to the `foo` but instead it refers to the rest of the arguments (anything after the first argument)

```js
function important(foo, ...numbers) {

	let message = 'foo is: ' + foo + ' AND ...numbers are: ' + numbers;
	return message;
}

console.log(important (1,2,3,'value'));
```

* more examples:

```js
// Since theArgs is an array, a count of its elements is given by the length property:
function fun1(...theArgs) {
  console.log(theArgs.length);
}

fun1();  // 0
fun1(5); // 1
fun1(5, 6, 7); // 3
```

##### Rest properties

```js
let { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 };

x; // 1
y; // 2
z; // { a: 3, b: 4 }
```

* in this example, a rest parameter is used to collect all arguments after the first one in an array. Each one of them is then multiplied by the first parameter and the array is returned:

```js
function multiply(multiplier, ...theArgs) {
  return theArgs.map(function(element) {
    return multiplier * element;
  });
}

var arr = multiply(2, 1, 2, 3);
console.log(arr); // [2, 4, 6]
```

#### Spread Operator

* it has exactly opposite action of the REST operator.
* it takes the array and then converts (split) them into a single arguments [1,2,3] ----> (1,2,3)

> * allows an iterable such as an array expression to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected, or an object expression to be expanded in places where zero or more key-value pairs (for object literals) are expected.

* For function calls

```js
myFunction(...iterableObj);
```

* For array literals

```js
[...iterableObj, 4, 5, 6];
```

* For object literals (new in ECMAScript; stage 3 draft)

```js
let objClone = { ...obj };
```

* more examples:

```js
// example1
function total(x,y,z) {
	return x + y + z;
}

let numbers = [1,2,3]
console.log(total(...numbers));

// example2 (Copy an array)
var arr = [1, 2, 3];
var arr2 = [...arr]; // like arr.slice()
arr2.push(4);

console.log(arr2); // [1, 2, 3, 4]
// arr remains unaffected


// example3 (concatenate arrays)
// old way
var arr1 = [0, 1, 2];
var arr2 = [3, 4, 5];

// Append all items from arr2 onto arr1
arr1 = arr1.concat(arr2);

// new way using spread
var arr1 = [0, 1, 2];
var arr2 = [3, 4, 5];
arr1 = [...arr1, ...arr2];

// example4
// old way
var arr1 = [0, 1, 2];
var arr2 = [3, 4, 5];
// Prepend all items from arr2 onto arr1
Array.prototype.unshift.apply(arr1, arr2) // arr1 is now [3, 4, 5, 0, 1, 2]

// new way
var arr1 = [0, 1, 2];
var arr2 = [3, 4, 5];
arr1 = [...arr2, ...arr1]; // arr1 is now [3, 4, 5, 0, 1, 2]

// example5
var obj1 = { foo: 'bar', x: 42 };
var obj2 = { foo: 'baz', y: 13 };

var clonedObj = { ...obj1 };
// Object { foo: "bar", x: 42 }

var mergedObj = { ...obj1, ...obj2 };
// Object { foo: "baz", x: 42, y: 13 }
```

##### Spread properties

```js
let { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 };
let n = { x, y, ...z };

n; // { x: 1, y: 2, a: 3, b: 4 }
```

* more examples:

```js
var parts = ['shoulders', 'knees'];
var lyrics = ['head', ...parts, 'and', 'toes'];  // ["head", "shoulders", "knees", "and", "toes"]
```
