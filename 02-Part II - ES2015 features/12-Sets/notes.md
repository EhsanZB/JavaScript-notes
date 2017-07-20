## Sets

> Set is a collection of values in which each one should be `unique`.

```js
let items = new Set(['one','two','three','one','two']);

console.log(items) // it returns only the unique values: ['one','two','three']
```

> see `__proto__` in the return object for full list of Set methods.

```js
items.add('ten');
console.log(items.size); // 4
console.log(items)
console.log(items.has('two')); // true

items.delete('one');
console.log(items.size); // 3

items.clear();
console.log(items)
console.log(items.size); // 0

items.add('first');
console.log(items)
console.log(items.size); //
```

* below is another way to `initiate a Set` (instead of passing the args to the constructor):

```js
let items3 = new Set();

items3.add('one');
items3.add('two');

console.log(items3);
console.log(items3.values()); // return a set iterator so we can use it for `for-of`

for (let i of items3) { console.log(i) };

// or using the 'embedded forEach method'
items3.forEach(item => console.log(item));
```

> using Spread operator to `convert the Set into an array`, so we can use array methods (like filters) on the result sets.

```js
let tags = ['javascript', 'php', 'vue', 'css', 'laravel', 'php','css'];

let tagsSet = new Set(tags);

console.log(tagsSet); // Set(5) {"javascript", "php", "vue", "css", "laravel"}

// now for example we want to show only tags with 3 letters! we need to filter through the set items but while set doesn't have such methods in its prototype or api, then we can use Spread operator to convert it to an array.

let filteredTags = [...tagsSet].filter(tag => tag.length === 3);

console.log(filteredTags); // ["php", "vue", "css"]
```

> IMPORTANT: note that after we've done with our manipulations or filtering, we probably need to convert the array into the Set type again:

```js
console.log(new Set(filteredTags)); // Set(3) {"php", "vue", "css"}
```
