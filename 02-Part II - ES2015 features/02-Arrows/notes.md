## Arrows (Arrow Functions)

* step1: delete `function`
* step2: insert `=>` after the brackets ()
* step3: delete () if there is ONLY one parameter: `(task)` changed to `task`
* step4: if there is no parameter then we should use only `()`
* step5: note that we CAN NOT omit the () if we have more than one parameter (task, index)
* step6: if the content of the function is ONLY one line, then the {} can be omitted. (inline version!)
* step7: note that `return` keyword in inline version of function is IMPLICIT, it means that we can omit it and it will be automatically handled.

> The context of the `this` keyword when using arrow functions, is `DIFFERENT!`. so in order to update our current project from old function to new one, it won't be as easy as just changing to arrows! be ware of the SCOPE of the `this` inside each function.

* using arrow function `this` binding NEVER changes.

> the value of `this` is changed in using function and NEVER changes in arrow functions!

```js
class TaskCollection {
	constructor(tasks = []){
		this.tasks = tasks;
	}

	// Old way
	log() {
		this.tasks.forEach(function(task){
			console.log(task);
		});
	}

    // new way
	log() {
		// this.tasks.forEach(task => console.log(task));
		this.tasks.forEach((task, index) => console.log(task.name,'@index:' + index));
	}

	important1() {
		// let that = this // this `this` is same as `this` from inside the function (only when using arrow function)
		this.tasks.forEach(task => {
			console.log(this);  // this refers to TaskCollection (it's exactly same `that`)
		});
	}

	important2() {
		this.tasks.forEach(function(task) {
			console.log(this);  // this refers to Window object (note that `use strict` is automatically applied)
		});
	}

}

class Task {
	constructor(name = ''){
		this.name = name;
	}
}

new TaskCollection([
	new Task('task1'),
	new Task('task2'),
	new Task('task3')
]).log();


new TaskCollection([
	new Task('task1'),
	new Task('task2'),
	new Task('task3')
]).important1();
```

* an example for step7:

```js
let names = ['Ehsan','Massih','Asghar','Gholaam'];

// Old way
greeting = names.map(function(name){
	return 'Hello, ' + name;
});


// New way
// note that `return` keyword is omitted!
greeting = names.map((name) => 'Hello, ' + name);

console.log(greeting);
```
