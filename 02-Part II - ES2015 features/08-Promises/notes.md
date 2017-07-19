## Promises

* it is a `placeholder` (holding spot) for an `operation` that has `not` been taken place.
* it's a `promise to do an action` - it hasn't done that yet! (it's `not the confirmation`! it just a promise!)
* while the promise is a `placeholder for an action` which is `not completed `yet, so once it has been completed, then we can use `.then` to proceed to the following action.

```js
var promise = this.$http.get('/some/path');
promise.then(function(data){
    // doing something
}).catch(function(err){
    // error handling
})
```

* note that we can also combine `.catch` with `.then` by passing it as the `second argument`:
* although `.catch` is omitted but while it's located on the `second args of .then`, so it will `triggered as .catch`.

```js
promise.then(function(data){
    // doing something
}, function(err){
    // error handling
});
```

#### resolve and reject

* resolve and reject `are functions` that we can `trigger` them based on the `result of the promise`.
* note that `without` calling `resolve()` or r`eject()`, the `.then` part won't execute!
* call reject() when an `error is thrown` (we need to be `explicit` about resolve and reject!)

```js
var timer = new Promise(function(resolve, reject) { // this function executes immediately (something like constructor!) - it's kinda bootstrap for our promise
	console.log('initiating Promise!!!!');
	setTimeout(function() {
		console.log('timeout done!');
		resolve();
	}, 2000);
});

timer.then(function() { // it won't execute if we forgot to put resolve() inside the promise function (also called as Executor function)
	console.log('doing something else after our timeout is done....');
})
```

* a better approach to the previous example:

```js
var timer = function(length){
	return new Promise(function(resolve, reject) {
		console.log('initiating Promise!!!!');
		setTimeout(function() {
			console.log('timeout done!');
			resolve();
		}, length);
	});
};


timer(3000).then(function() {
	console.log('doing something else after our timeout is done....');
});
```
