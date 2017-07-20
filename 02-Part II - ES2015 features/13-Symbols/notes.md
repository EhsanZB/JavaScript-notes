## Symbols

> The data type `symbol` is a `primitive data type` having the quality that values of this type can be used to `make object properties` that are anonymous.  This data type is `used as the key` for an object property when the property is intended to be `private`, for the internal use of a class or an object type.

* A value having the data type "symbol" can be referred to as a `"symbol value"`.

> a symbol value is created by invoking the `function Symbol()`, which `dynamically produces an anonymous, unique value`.

* The only sensible usage is to store the symbol and then use the stored value to create an object property.

```js
var  myPrivateMethod  = Symbol(); // stores the symbol in a 'var'
this[myPrivateMethod] = function() {...};
```

> When a symbol value is `used as the identifier in a property` assignment, the property (like the symbol) is `anonymous`; and also is `non-enumerable`.  Because the property is non-enumerable, it will not show up as a member in the loop construct "for( ... in ...)", and because the property is anonymous, it `will not show up` in the result array of "Object.getOwnPropertyNames()".

* Symbol values provide a way by which `custom classes can create private members`, and maintain a symbol registry that pertains just to that class.

> there is no ECMAScript 5 equivalent for symbol.

```js
Symbol("foo") !== Symbol("foo")
const foo = Symbol()
const bar = Symbol()
typeof foo === "symbol"
typeof bar === "symbol"
let obj = {}
obj[foo] = "foo"
obj[bar] = "bar"
JSON.stringify(obj) // {}
Object.keys(obj) // []
Object.getOwnPropertyNames(obj) // []
Object.getOwnPropertySymbols(obj) // [ Symbol(), Symbol() ]
```

* [Source:MDN Glossary](https://developer.mozilla.org/en-US/docs/Glossary/Symbol)
