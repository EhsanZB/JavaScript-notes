## String additions

```js
// ES5 example
var title1 = 'Red Rising.';
if (title1.indexOf('Red' === 0)) {
	console.log('existed!');
}
```

* ES6 new string methods:

    * .includes()
    * .startsWith()
    * .endsWith()
    * .repeat()

#### .includes()

```js
let title2 = 'Red Rising.';
if (title2.includes('ising')) {
	console.log('existed!');
}else{
	console.log('NOT existed!');
}
```

#### .startsWith()

```js
let title = 'Red Rising.';
if (title.startsWith('Ri',4)) { // the second arg is optional and it shows the start index - position -  (note that it's CASE-SENSITIVE )
	console.log('existed!');
}else{
	console.log('NOT existed!');
}
```

#### .endsWith()

```js
let title3 = 'Red Rising.';
if (title3.endsWith('ing.')) {
	console.log('existed!');
}else{
	console.log('NOT existed!');
}
```

#### .repeat()

```js
let str = 'lol';
console.log(str.repeat(5)); // lollollollollol

let str1 = 'Hello';
let str2 = 'o';
console.log(
	// str1 + str2.repeat(10) + '.'
	`${str1}${str2.repeat(10)}.` // Hellooooooooooo.
);
```

* another example

```js
let heading = 'This heading is here';
console.log(
	`${'=>'.repeat(5)} ${heading} ${'<='.repeat(5)}` // =>=>=>=>=> This heading is here <=<=<=<=<=
)
```
