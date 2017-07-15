## Arrays

> 'Some Definitions'

#### Arrays are ...
* `untyped`: an array element may be of any type and different elements of the same array may be of different types.
* `zero-based`: and and use 32-bit indexes, so maximum number of elements of an array would be (2^32 - 2)
* `dynamic`: they grow and shrink as needed
* Arrays are special form of javascript object (note that access to numerically indexed array elements is `faster` than access to regular object properties)

> 'creating arrays using array literal [element1, element2, element3, ...]'

```js
var myArray1 = []; // an empty array
var myArray2 = [1,2,"3",{x:4,y:5},[6,7],9,10]; // elements can be any type
// values in array literal do not need to be constant!
var base = 1024;
var myArray3 = [1,base,base+4,-base,"23"];
```
* Arrays ca be 'sparse': when an array literal contains 2 commas (,,) in a row --> it means that an element is missing.
* missing elements are 'undefined'.

```js
console.log(cnt.length); // 3 (the element is missing but its considered in length
console.log(cnt[0]); // 1
console.log(cnt[1]); // undefined
console.log(cnt[2]); // 3

// note that in JS the tailing commas in arrays is allowed
var cnt1 = [1,2,];
console.log(cnt1.length); // 2

var cnt2 = [1,2,,]; // creating sparse area at the end of the array
console.log(cnt2.length); // 3
```

* Here is another way of array literal to assign the elements to the array:

```js
var myList = [];
myList[0] = 1;
myList[1] = "2";
myList[2] = {x:2,y:3};
console.log(myList.length); // 3
```

> 'creating arrays using 'Array Constructor'  by invoking the constructor Array();'

```js
// way#1
var myArray4  = new Array(); // this is same as array literal of []
// way#2
var myArray5 = new Array(3); // 'pre-allocate' elements for this array (note that such elements and their respective indexes are not even defined!)
// way#3
var myArray6 = new Array(1,2,"3"); // in this way the constructor arguments become the elements of the array
```

* note that the 'length' property which is the number of elements of an array is 'writable' --> is setter and getter

```js
var testArray = ['A','B','C','D','E'];
console.log(testArray.length); // 5 elements
console.log(testArray[2]); // C
console.log(testArray[3]); // D

testArray.length = 3;
// here at this point the length is set to 2 elements only so the rest elements (which are located at greater index number) are deleted
console.log(testArray.length); // 3
console.log(testArray[2]); // C
console.log(testArray[3]); // undefined
```

> 'iterating' arrays

* remember that the Object.keys(obj) method returns an array of a given object's own enumerable properties.
* note that NONE of these methods modify the original array (does not mutate the original array)
* we can modify the array inside the function we pass to the array method, but the method itself does not modify the original

```js
var arr = ['A',2,'Ehsan',34];
var keys = Object.keys(arr);
console.log(keys); // ["0", "1", "2", "3"]
console.log(keys.length); // 4
```

```js
// way#1
for (var i = 0; i < keys.length; i++){
   var key = keys[i];
   console.log(arr[key]);
}

// way#2
for (var item in arr){
   console.log('Index: ' + item + ' -> ' + 'Value: ' + arr[item]);
}

// way#3
// syntax: array.forEach(callback[, thisArg])

```
##### Array.prototype.forEach(callback[, thisArg])

* Function to execute for each element, taking three arguments: currentValue,index,array
* this function is not invoked for index properties that have been deleted or are uninitialized (i.e. on sparse arrays).
* The range of elements processed by forEach() is set before the first invocation of callback.
* Elements that are appended to the array after the call to forEach() begins will not be visited by callback.
* example#1: note that the function arguments can be any name (look at the example#2 in which the 'value' is equivalent to 'element' in this example.

```js

// example#1
arr.forEach(function (element,index,array) {
  console.log('Index: ' + index + ' -> ' + 'Value: ' + element);
  // or
  console.log('Index: ' + index + ' -> ' + 'Value: ' + array[index]);
});

// example#2
var a = [1,2,3];
var sum = 0;
a.forEach(function addNumber(value){
  sum += value;
});
console.log(sum); // 6 (1+2+3)

```

* `thisArg` is an object to which the `this` keyword can refer in the `callback` function
* If a `thisArg` parameter is provided to forEach(), it will be passed to callback when invoked, for use as its this value.
*  Otherwise, the value undefined will be passed for use as its this value.

```js
var myObject = {
    resultLabel : 'The result is: ',
    showResult : function(elm,index){
        console.log( this.resultLabel + 'Index: ' + index + ' -> ' + 'Value: ' + elm);
    }
};

// way#1
a.forEach(myObject.showResult,myObject);

// way#2 (same result as way#1)
a.forEach(function(elm,index){
    this.showResult(elm,index);
},myObject);
```


* Array.isArray() -->  returns true if an object is an array, false if it is not.

```js

console.log(Array.isArray([])); // true
console.log(Array.isArray({})); // false

```

##### Array.prototype.map(callback[, thisArg])
