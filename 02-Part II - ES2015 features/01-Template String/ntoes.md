## Template String

* it also called as TEMPLATE LITERAL
* use BACK-TICK to implement the Template string in ES6!

> the indentation (and tabs) `take affect` when using template string (can use `.trim()` to delete extra white spaces.


```js
// OLD way (just as an example!)
// note that such indentation is just to fake it for illustration purposes!

let template1 = [
	'<div class= "alert">',
		'<p> Hello </p>',
	'</div>'
].join(''); // using empty string `''` in order to delete `,` between each item of the array!

console.log(template1);

// ES6 version
let message = 'Hello World!';
let template2 = `
	<div class= "alert">
		<p> ${message} </p>
	</div>
`;

 console.log(template2);
```

> we can also use `ESCAPING` in the template but also instead we can simply for example press Enter instead of using `\n`.

```js
// in this example message 2 and 3 have same result.

let name = 'Ehsan';
let greet = 'fine';

let message2 = `Hello, ${name}.\nI hope you are ${greet}.\n\tCan't wait any more!`;
let message3 = `Hello, ${name}.
I hope you are ${greet}.
	Can't wait any moreeee!`;

console.log(message3);
```
