## Class

* in object-oriented programming, a class `defines an object's characteristics`.
* Class is a `template definition` of an object's `properties` and `methods`.
* remember that object is a unique set of properties.
* `class of objects`, share certain properties -> `members` (instances) of the class have their own properties to hold or define their state
* but they also have properties that define their `behaviors` --> this behavior is defined by a class and it's shared by all instances.

> classes are based on JS's prototype-based inheritance mechanism

* if two objects inherit properties from the same prototype object, then we can say that they are `'instances'` of the same class.
* so if two object `inherit from the same prototype` --> it means that they were created and 'initialized' by the `same constructor` function.

> JS classes and prototype-based inheritance mechanism are substantially different form the classes and class-based inheritance of java or other similar programming language.

* in javascript, class is a `'set of objects'` that inherit properties from the `same prototype object`.
* if we define a prototype object and then use `Object.create()` to create objects that inherit from it, so we actually have `defined a JS class`.
* instances of a class require `initialization` --> it's common to define a function that creates and initialize the new object (called as `'factory' function`).
* Object.create('prototype object'); --> used in factory function to create an object that `inherits from the prototype object`.
* this prototype object is `stored as a property` of the factory function.
* it also defined the shared methods (behaviors) for all range objects (see the example below)
* the use of `'this' keyword` in this example is important, because it's common to use 'this' in classes like in this example.

> prototype is fundamental to the identity of a class. constructor initialize the `state of the new object`. the `name of the constructor` function is usually adopted as the `name of the class`.

* it's common to make a separate js file for each specific class.
* in the example below, the whole codes are saved into `range.js` and this is our class which representing a range of values.
* the class contains `factory function` and `methods` which are `define by the prototype object`.* note that this example is one way to `create JS class` (but in fact this example is not good way because we do not apply constructor function).
* range.js -> a class representing a range of values
* note that in this example, a property of the range() factory function (range.methods) has been used to `store the prototype object` that defined the class.

```js
// defining the 'factory function'
  function range(from,to){
      var r = Object.create(range.methods);
      // defining from and to properties for r object
      // note that these properties are 'unshared' and 'non-inherited' properties
      // they define the unique state of each individual range object
      // (all shared and inherited methods are defined in range.methods (the prototype object)
      r.from = from;
      r.to = to;

      return r; // returning the new object
  }

  // defining the 'prototype object' (in which it defined the methods -> inherited by all range objects)
  range.methods = {

      // return true if x is in the range (otherwise, false)
      includes : function(x){
          return (this.from <= x && x <= this.to);
          // this --> Object {from: 2, to: 8}
      },

      // return a string representation of the range
      toString : function(){
          return "(" + this.from + "...." + this.to  + ")";
      }
  };

  // creating a new instance of the class
  var instance = range(2,8);

  console.log(instance); // Object {from: 2, to: 8}

  console.log(instance.includes(3)); // true (3 is in the range! between 2...8
  console.log(instance.includes(9)); // false (9 is not in the range! between 2...8
  console.log(instance.includes(2.342)); // true (2.342 is not in the range! between 2...8
  console.log(instance.toString()); // (2....8)
  ```

 > a 'constructor' is a function designed for the 'initializing' the `newly created objects`. also remind that constructors are` invoked using 'new' keyword` --> automatically create the new object, so there will be `no need to call Object.create()` to take any other action to create the new object --> accessible with `'this'`.

 * constructor function merely has to initialize 'this' ( and `do not have to create or return an object`).

  * `'prototype property'` of the constructor function is used for the `property of the new object`.
  * so, all objects created with the same constructor, inherit from the same object and also they are `members of the same class`.
  * in the example below, instead of using factory function, we apply c`onstructor function` to initialize the new range object.
  * it's important to note that here in the class, the `constructor does not create or return the object` (it just initialize it).
  * note that the `constructor` functions are written in `Capital letter`.
  * in this example, an invocation of Range() constructor, `automatically uses 'Range.prototype'` as the prototype of the new Range object, so that's why we can use instance.includes();

  ```js
  function Range(from,to){

     // define non-inherited properties (unique to this object only) by storing the 'start' and 'end' points ('state') of the new object

     this.myfrom = from;
     this.myto = to;

     // it was actually e.g, this.from = from; but in order to distinguish which from is which from I changed the name to myform!

 }

 // all range objects inherit from this object
 // note that the property name should be 'prototype'

 Range.prototype = {

     constructor: Range, // explicitly set the constructor

     includes : function(x){
         return (this.myfrom <= x && x <= this.myto);
     },

     toString : function(){
         return "(" + this.myfrom + "...." + this.myto  + ")";
     }
 };


 var instance2 = new Range(2,8);
 console.log(instance2.includes(7)); // true


 // note that the 'instanceof' operator does not actually check whether 'instacnce2' was initialized by the Range constructor or not!

 // 'instanceof' operator, checks whether it inherits from 'Range.prototype'.
 console.log(instance2 instanceof Range); // true
 ```

 > any JS function can be used as a constructor (constructor invocations need a 'prototype' property)

 * in fact, Range.prototype was set to a new object which contains methods for our class, actually such methods can be expressed as 'properties' of a `single object literal`.
 * so every JS function automatically has a `'prototype' property` --> the value of this property is a `'function object'` (which has a single and un-enumerable property called as '`constructor`').

> All objects inherit a `'constructor property'` from their prototype.

* `'Object.prototype.constructor'` -> Returns a `reference` to the 'Object function' (that created the instance's prototype).
* objects inherit a constructor property that refer to their constructor (whatever their constructor function's prototype has or inherits (like prototype.constructor), then the objects (instances) also refer to that.
* so the 'constructor property' of the prototype object actually gives the `'class of an object'`.

```js
// example1
var F = function(){}; // F is a function object
var P = F.prototype; // P is the F's prototype object

console.log(P.constructor === F); // true


// example2
var o = {};
console.log(o.constructor === Object); // true

var a = [];
console.log(a.constructor === Array); // true

var n = new Number(3);
console.log(n.constructor === Number); // true


// example3
function Tree(name) {
    this.name = name;
}

var theTree = new Tree('Redwood');
console.log('theTree.constructor is ' + theTree.constructor);

// here is what console logs:
theTree.constructor is function Tree(name) {
   this.name = name;
}
```

* there is `another way to set the constructor` instead of explicitly set in the prototype.
* using the `'predefined prototype object'` with its constructor property and then adding methods to it one at a time.

```js
// just extending the predefined Range.prototype object (no overwrite the Range.prototype.constructor)
Range.prototype.includes = function(x){
    return (this.myfrom <= x && x <= this.myto);
};
```
