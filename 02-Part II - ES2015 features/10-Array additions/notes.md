## Array additions

```js
// ES5
console.log(
	[2,5,10,4,7,8,13,15].indexOf(10) //2
)

console.log(
	[2,5,10,4,7,8,13,15].indexOf(10) > -1 // true
)
```

* new ES6 Array methods:

    * includes()
    * find()   * when we need to use a CONDITION
    * findIndex()
    * .fill()
    * .keys()
    * .values()
    * .enteries()

#### .includes()

```js
console.log(
	[2,5,10,4,7,8,13,15].includes(25) // false (there is no 25 in the array)
)
```

#### .find()

```js
console.log(
	[2,5,10,4,7,8,13,15].find(function(item){
		// condition
		// return  item === 7 // return the FIRST item that meets this condition
		// return item > 8 // 10 (note that although 13 is greater than 8 but .find method starts from the beginning of the array and stops when meets the criteria)
		return item % 2 !== 0 // 5
	})
)
```
* another example: the objective of this example is to find the user(s) who is admin.

```js
class User {
	constructor(name, isAdmin) {
		this.name = name;
		this.isAdmin = isAdmin;
	}
}

let users = [
	new User('Massih', false),
	new User('Ehsan', true),
	new User('Alex', false)
];

// find the first user that is admin
console.log(
	users.find(user => user.isAdmin) // {name: "Ehsan", isAdmin: true}
	users.find(user => user.isAdmin).name // Ehsan
)
```

#### .enteries()

> note that when using .enteries(), the items.indexOf() won't work

```js
// without .enteries()
let items = ['item1', 'item2', 'item3'];
for (let item of items) {
	console.log(
		`${item} with index of: ${items.indexOf(item)}`
	)
}

// using .enteries()
let items = ['item1', 'item2', 'item3'].entries();
for (let item of items) {
	console.log(
		`${item}` // returns: index,item  for example (0,item1,1,item2,...)
	)
}
```
