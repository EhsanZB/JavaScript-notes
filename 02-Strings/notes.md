## Strings

* Strings are `immutable` in JS.
* Strings can be treated like read-only arrays.
* so we can `access` individual characters (16-bit) from a string `using [ ]`. It's a better way instead of using charAt( );
* The `String global object` is a constructor for strings, or a sequence of characters.

#### properties:

> length( );

* String length property is zero-based.

```js
var str = 'Hello, my name is Ehsan.';

console.log(str.length);         // 24
console.log(str[0]);             // H
console.log(str[str.length-2]);  // n
```

#### methods:

> toUpperCase( ); / toLowerCase( );

```js
console.log(str.toUpperCase()); // HELLO, MY NAME IS EHSAN.
console.log(str.toLowerCase()); // hello, my name is ehsan.
```

> charAt(index);

* Returns the character of the specified position.

```js
console.log(str.charAt(0));            // H
console.log(str.charAt(str.length-2)); // n
```

> indexOf(string,start);