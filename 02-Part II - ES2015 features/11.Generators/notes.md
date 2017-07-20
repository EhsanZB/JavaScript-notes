## Generators

* it allows functions to `exit/pause at a certain point` (set of state) and resume it later!
* to demonstrate that a function is a generator, we add `*` before function name  - anywhere between function and its name - even with space - e.g: `function * numbers(){}`
* `yield` keyword is something like `return` but we can have multiple yield and ability to cycle through them (`pause/resume`).

> Generators gives us the ability to exit/pause at the particular point, but later, we can resume execution using the `exact same state that we had before`!

```js
function *numbers() {
	console.log('begin...');  
	yield 1;
	yield 2;
	yield 3;
}

numbers(); // it won't show anything!!
let iterator = numbers();
```

* the response of `.next()` is not a value we specify in the yield, instead it return an object containing the `value of the next iterator` and the status of whether or not the generator is complete or done! it means that there are `no more yield left in the generator`.

```js
console.log(iterator.next()); // {value: 1, done: false}

//note that it just pauses the execution and it never forget the state and it waits for our command to resume and go to the next iteration.

console.log(iterator.next().value); // 1 (with the first next(), the generator execute everything from above until the first yield and paused there)

console.log(iterator.next().value); // 2 (resume 1, execute the second yield and paused there )

console.log(iterator.next().value); // 3
```

* another example:

```js
function * range(start, end) {
	while (start <= end) {
		yield start;

		start++; // remember that using the generators, the state of the values never forget!
	}
}

let iterator = range(1,3);
console.log(iterator.next()); //1 (done: false)
console.log(iterator.next()); //2 (done: false)
console.log(iterator.next()); //3 (done: false)
console.log(iterator.next()); // undefined (but the done status is `true` which means that there are no more paused yield)
```

> `for-of` understands generators and `automatically fetch the values` (value of each iteration) for us.

```js
for (let i of iterator) {
	console.log(i) // 1 2 3 (each on separate lines in the console)
}

// using Spread operator
console.log(
	[...range(1,5)] // [1, 2, 3, 4, 5] 0:1,1:2,...
);
```
