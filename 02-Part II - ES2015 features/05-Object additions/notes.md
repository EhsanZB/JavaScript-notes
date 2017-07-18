## Object additions


#### Object Shorthand

* if the key and the value of an object are same, so the VALUES can be OMITTED!

```js
function getPerson(){
	let name = 'Ehsan';
	let age  = 35;

	// assume that we want to return an object here
	// note that here, the key is `name` and the value (refers to let name = ....) is also `name`
	// Old way (ES5)

	// return {
	// 	name : name,
	// 	age  : age
	// }

	// New way (ES6)

	// return {
	// 	name,
	// 	age	 
	// }

	// also can be further concised into: (by deleting the extra white spaces!)
	// return { name, age }

	// Method Shorthand
	// such shorthands also can be used when defining method inside an object

	return {
		name,
		age,
		greet1: function () { // ES5 version
			return 'Hello ' + this.name + '.';
		},
		greet2() { // ES6 version
			return `Hello ${this.name}.`
		}
	}
}

console.log(getPerson());
console.log(getPerson().greet1());
console.log(getPerson().greet2());
```

#### Object Destructuring

```js
let person = {
	name : 'Ehsan',
	age  : 35,
	info : [],
	contact : 123
}

// ES5
var name = person.name;
var age  = person.age;

// ES6
// destructure whatever we need/want (no need to extract all keys in the object!)
let { name, age, contact } = person;

console.log(name); // Ehsan
console.log(age);  // 35
console.log(contact);  // 35
```

> we can also use object `destructuring` as a `Function Argument`, this capability of ES6 can be useful in `ajax call`!

```js
// ES5
function getData(data) {
	var name = data.name;
	var age  = data.age;

	console.log(name, age)
}


// ES6
function getData({ name,age }) {

	console.log(`Hello ${name}, you are ${age}.`);
}


// fill with dummy info
getData({
	name : 'Ehsan',
	age  : 35
})
```

> remember that if we have same function name in our js code, the one which is located bottom will be overwritten on its top one, so it's like executing the second one and ignore the first one!
