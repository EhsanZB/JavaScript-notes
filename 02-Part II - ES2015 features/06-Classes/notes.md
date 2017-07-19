## Classes

> ES6 class, is just a syntatic sugar over the old way we used to handle it, so actually behind the scene, the method will be added to the class using the prototype!

```js
class Person{
	constructor(fname, lname){ // assigning properties in the constructor
		this.fname = fname;
		this.lname = lname;
	}

	getFullName(){
		// return this.fname + ' ' + this.lname;
		return `${this.fname} ${this.lname}`;
	}


	// static method: only callable outside the class and cann't be referenced from inside (or another method)
	static register(...args) { // rest (accepts all arguments when registering a new user)
		return new Person(...args) //spread (pass all arguments to the constructors' arguments - which are already in an array format)
	}
}


let person1 = new Person('Ehsan','ZB');
console.log(person1.getFullName());

let person2 = new Person();
person2.fname = 'Massih';
person2.lname = 'Hazratoo';
console.log(person2.getFullName());

// note that while we are calling a static method, we won't need to create an instance of a class with new keyword! (just directly call the method)
let person3 = Person.register('asghar', 'asghar@example.com');
console.log(person3);
```

#### ES5 (making a class)

> remember about the side effect and downsides of defining the method inside the constructor function in which, it will be redefined (recreate) for each instance of the user (in this example, user) --> memory problem! instead, it's recommended to attach the method to the prototype, so every instance of the user will SHARE the method (rather than recreating it in memory)

```js
// 1. define the constructor function
function User(username, email) {
	this.username = username;
	this.email = email;
}

// 2. add a method to the class
User.prototype.changeEmail = function(newEmail) {
	this.email = newEmail;
}

let user = new User('Ehsan','ehsan@example.com');
user.changeEmail('foo@example.com');

console.log(user);
console.dir(user);
```

> note that classes are FIRST CLASS CITIZEN in ES6! so we can pass them around anywhere. for example we call pass a class as an argument. (it can be passed though as an function argument)

```js
function log(strategy) {
	strategy.handle();
}


// way#1
log(new class {
	handle() {
		console.log('handling .....');
	}
});



// way#2
class ConsoleLogger {
	handle() {
		console.log('handling .....');
	}
}

log(new ConsoleLogger);
```
