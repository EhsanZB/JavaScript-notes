## Date and Time

* `Date objects` are based on a time value that is the number of milliseconds since 1 January, 1970 UTC.
* Date objects can only be `instantiated` by calling JavaScript Date as a `constructor`.
* Date objects have `no literal syntax`.

> _If no arguments are provided, the constructor creates a JavaScript Date object for the `current date and time` according to system settings._

* if more than one argument, the specified arguments represent `local time`.
* months are `zero-based`.
* `UTC` (Universal Time), also known as Greenwich Mean Time (GMT), refers to the time as set by the World Time Standard


#### Date constructors:

1. new Date( );
2. new Date(value);
3. new Date(dateString);
4. new Date(year, month[, day[, hour[, minutes[, seconds[, milliseconds]]]]]);

* `dateString`: String value representing a date. It should be in a format recognized by the Date.parse( ) method.

```js

var date1 = new Date();
var holiday = new Date('December 25, 2015');
var date2 = new Date(1997,0,1); // January, 1 1997

```


#### Date methods:

> Date.now( );

* returns the number of milliseconds elapsed since 1 January, 1970 00:00:00 UTC.

> Date.parse( );

* Parses a string representation of a date and returns the number of milliseconds since 1 January, 1970 00:00:00 UTC.

> UTC:

1. Date.UTC(year, month[, day[, hour[, minute[, second[, millisecond]]]]])
2. Date.UTC( );

* returns the number of milliseconds in a Date object since January 1, 1970, 00:00:00, universal time.

```js
console.log(Date.now());                   // e.g: 1462315841357
console.log(Date.parse("26/august/1981")); // e.g: 367657200000
console.log(Date.UTC(1981,0));             // e.g: 347155200000
```

#### Date property:

> Date.length;

* The value of Date.length is always 7. This is the number of arguments handled by the constructor.

```js
console.log(Date.length); // 7
```

#### Date.prototype GETTER Methods:

> getDate( );
