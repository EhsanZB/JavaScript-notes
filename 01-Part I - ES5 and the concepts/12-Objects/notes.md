## Objects

> Object-oriented programming (OOP) is a programming paradigm that `uses abstraction to create models` based on the real world.

* JavaScript is a `prototype-based language` and contains no class statement, such as is found in C++ or Java.
* Instead, JavaScript uses functions as `constructors` for classes.

#### Object

* it `aggregates multiple values` (primitive values or other objects) and allow us to store and retrieve those values `by name`.
* it's unordered collection of properties, each of which has a `'name'` and `'value'`. (property names are string)
* `Property` values can be values of any type, including other objects (an expression that may include primitive or other types)
* Properties are identified using `'key values'`. A key value is either a `String` or a `Symbol` value.
* There are two types of object properties which have certain attributes: The 'data property' and the 'accessor property'.
* `data property` : Associates a key with a value
* `accessor property` : Associates a key with one or two accessor functions (get and set) to `retrieve` or `store` a value.
* in addition to maintaining its own set of properties, object also `inherits from another object known as 'prototype'`.
* the methods of an object typically inherit from prototype (such methods are actually inherited `properties` of prototype object)
* In JavaScript there are `6 primitive types`:
    undefined
    null
    boolean
    string
    number
    symbol
* Everything else is an object!

```js
typeof Boolean(true); // "boolean"
typeof new Boolean(true); // "object"
```

> A primitive (primitive `value`, `primitive data type`) is data that `is not an object` and `has no methods`. All primitives are `immutable` (cannot be changed). (note that `objects are mutable`)

#### Creating an empty object

```js
// way#1 : using object literal
var obj1 = {}; // an empty object

// way#2 : using 'new' keyword and make an class instance (new object) using constructor invocation
var obj2 = new Object(); // creates a new object with the specified prototype object and properties.

// way#3
var obj3 = Object.create(Object.prototype); // syntax:  Object.create(proto[, propertiesObject])


// note that Object.create() is a static function and it is not a method invoked on individual objects
// also note that instead of 'Object.prototype' that make an empty object, we can specify our own prototype
var obj = Object.create({x:1,y:4}); // in this case, obj inherits x and y properties (obj.x = 1)
```

> note that the 'property name' is an `'identifier'` in objects. for 'non-identifier' names, it's recommended to use double quotation.

```js
var point = {
    x : 302.3,
    y : 13.22
};

var book = {
    "title" : "Javascript fundamental",
    "for" : "all audiences"
};
```


* when creating objects with 'new', the 'new' operator creates and initialize a new object.
* the new keyword should be followed by '`function invocation'`. such functions is called as `'constructor'` functions and serves to initialize a newly created object
* JS has built-in-constructors (new Object(), new Array(), new Date()).

#### prototype

* every javascript object has a `second javascript object` associated with it call as `'prototype'`.
* an object `inherits its properties` from the prototype.
* the object created by 'new Object()' and object created by object literal {}, both `inherit form 'Object.prototype'`
* note that the objects `created by constructor invocation`, us the 'value' of the prototype property (of the constructor function) as their prototype.
* for example, var dateObj = new Date(); --> the dateObj object actually uses 'Date.prototype' as its prototype (inherits from Date.prototype)
* besides, the 'Date.prototype' also inherits properties from 'Object.prototype' --> so the 'dateObj' inherits form both Object and Date prototypes.
* such linked series of prototype objects is known as `'prototype chain'`.

> in javascript the only object that `has no prototype` and does not inherit any properties is: 'Object.prototype'. all of the javascript `built-in constructors` inherit properties form Object.prototype.

#### properties in objects

* generally speaking, javascript objects have a set of `'own properties'` and also inherit a set of properties from their `'prototype'`.

### query and setting of object properties

* prototype allows us to `add property and method` to our object.
* objectName.prototype.newPropertyName = anyValue;
* objectName.prototype.newMethodName = function(){...};

```js
var book = {
    "title" : "Javascript fundamental",
    "for" : "all audiences"
};

// get
console.log(book.title); // Javascript fundamental
console.log(book["title"]); // Javascript fundamental

// set
book.title = "JS fundamental 2nd edition";
console.log(book.title); // JS fundamental 2nd edition

book["title"] = "JS 3rd edition";
console.log(book.title); // JS 3rd edition

console.log(book); // Object {title: "JS 3rd edition", for: "all audiences"}

book.totalSales = 12000; // add totalSales property to the object and assign the value to it.
console.log(book.totalSales); // 12000
```

#### property inheritance

* suppose we query the property 'x' in the object 'o'.
* if 'o' does not have an `own property` with that name 'x', then the `'prototype object'` of 'o' is now looking (query) for the property 'x'.
* if the property object also does not have an own property name with that name ('x'), then query its 'prototype' --> query on `'prototype of prototype'`.
* the process continues until the property 'x' found, otherwise, an object with `null property will be returned`.
* to delete a property we user `delete` keyword. note that delete operator `only deletes 'own properties'` and not inherited ones. to delete the inherited ones we need to delete them from the prototype object in which it is defined.

```js
delete book.for;
console.log(book); // Object {title: "JS 3rd edition", totalSales: 12000}
```

#### testing properties

* while objects can be thought of as `'sets of properties'`, so it would be useful if we `test for 'membership'` in the set.
* it refers to the fact that the object whether `has a property with a given name` in the test.
* to do such testing we can use: '`in'`,`'hasOwnProperty()'`,`'propertyIsEnumerable()'`

> Ownership of properties is determined by whether the property belongs to the object directly and not to its prototype chain.

* enumerable properties are those properties whose internal [[Enumerable]] flag is set to true.
* enumerable properties show up in `for...in loops` unless the property's name is a `Symbol`.
* note that `'in'` can `distinguish between properties` that `do not exist` and properties that exist but have set to `undefined`. so in general, using 'in' is recommended upon using `!==`

> all `built-in methods` that objects `inherit` are not enumerable and they are non-enumerable.

* the properties that our code adds to the objects are enumerable, unless we make them non-enumerable (using some sort of functions)
* in fact in ECMAScript 5, there is `no way` to make such adds to non-enumerable

> `method is property of an object` which the value expression is a function.

```js
var o = { x : 1, y : undefined };

console.log("x" in o); // true
console.log("y" in o); // true
console.log(o.x !== undefined); // true
console.log(o.y !== undefined); // false

console.log("z" in o); // false (z does not exist)
console.log("toString" in o); // true ('toString' method is inherited from prototype and it's not the 'own property'.


console.log(o.hasOwnProperty("x")); // true
console.log(o.hasOwnProperty("z")); // false
console.log(o.hasOwnProperty("toString")); // false (it's inherited not owned)

console.log(o.propertyIsEnumerable("x")); // true
console.log(o.propertyIsEnumerable("y")); // true

o.title = "new edition";

console.log(o.propertyIsEnumerable("title")); // true
console.log(o.propertyIsEnumerable("toString")); // false (toString is not a enumerable method)



// using for-in to iterate through every property of an object
for (p in o){
    console.log(p); // x,y,title
}


// find methods in an object:  
for (p in o){
  if (typeof o[p] === 'function'){
      // ...
  }
}
```

#### enumerate property names:

> Object.keys()

* returns `only enumerable properties` of an object.
* `returns an 'array'` of a given object's own enumerable properties, in the same order as that provided by a `for...in` loop.
* for-in loop enumerates properties in the prototype chain as well.

> Object.getOwnPropertyNames()

* returns `all properties` including non-enumerable properties
* returns an array of all properties (enumerable or not) `found directly upon a given object`.

```js
var arr = ['a', 'b', 'c'];

console.log(Object.keys(arr)); // ['0', '1', '2'] --> the key for each value (as index)

// array like object
var myObj = { 0: 'a', 1: 'b', 2: 'c' };

console.log(Object.keys(myObj)); // ['0', '1', '2'] --> property name (key) of each property (do not confuse with the previous example which was index)

var an_obj = { 100: 'a', 2: 'b', 7: 'c' };
console.log(Object.keys(an_obj)); // ['2', '7', '100']

var myObj1 = { 0: 'a', 1: 'b', 2: 'c', "name": "Ehsan" };
console.log(Object.getOwnPropertyNames(myObj1).sort()); // ["0", "1", "2", "name"]

// Logging property names and values using Array.forEach
// elm -> property names
Object.getOwnPropertyNames(myObj1).forEach(function(elm, index) {
    console.log(elm + ' (index: ' + index + ')' + ' --> ' + myObj1[elm]);
});
```
