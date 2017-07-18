## Default Parameter

* Old way (ES5):

```js
function applyDiscount(cost, discount) {
	discount = discount || .10;
	return cost - (cost * discount);
}

console.log(applyDiscount(100)); // 90 (using default 10% discount)
```

* New way (ES6)

```js
function applyDiscount(cost, discount = .10) {

	return cost - (cost * discount);
}

console.log(applyDiscount(100)); // 90 (using default 10% discount)
```

> note that such default values are not limited to primitive values, it also accepts other values even from another function!

```js
function defaultDiscount() {
	return .10;
}

function applyDiscount(cost, discount = defaultDiscount()) {

	return cost - (cost * discount);
}

console.log(applyDiscount(100)); // 90 (using default 10% discount)
```
