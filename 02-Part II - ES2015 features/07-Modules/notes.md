## Modules

* module is just a `file` which `exports its behaviors`.
* rather than doing the way that we conventionally list down our js source files (e.g before the closing body tag),  in which need to be aware of their ordering which may depend upon each other!, we can implement modules using ES6 syntax, in which we will find the module, `export` its `behaviors`, and then import such behaviors `anywhere` it's necessary.
* we need to `expose` the behaviors (functionalities) out side the module (using `export` keyword )
* in this example, `TaskCollection.js` is a module.

> conventionally instead of ES6 module, we could use `commonJs`, `AMD`, `UMD`.

#### importing module (using `require`)

```js
// new way (Old approach) (using commonJs concepts!)
var TaskCollection = require('./TaskCollection');
```

#### importing module (using `import`)

* note that in order to use import we might need to implement `Roolup`, `Browserify`, `Webpack` or other tools in which they can read all the module contents and compile it into a single file, so all `browsers can understand it`!

```js
// New Approach (using import)
import TaskCollection from './TaskCollection';

// another example:
import { TaskCollection, foo } from './TaskCollection';
```

> note that if we get an error regarding `import` and `export` we need to add babel presets into our package file. then we need to add this preset in our gupl file (configuration of babelify)

* tip: `npm init -y` (ignore the interactive process of making a `packagejson` file)

```bash
 $ npm install babel-preset-es2015 --save-dev
```

>  note that if we use `export default` then we can `omit` the {}, but if we have any other exports within the module, then we need to put that value `inside` the {}

```js
import TaskCollection, { foo } from './TaskCollection';
```

> in ES6 we can export as much as we want (`opposite` of commonJs), it means that for example we can have both export the class and also export another variable at the same time in a single module js file (like TaskCollection in the example).

* exporting multiple values: the `value` of what we are `exporting` is `what we import` (export let foo = 'bar') --> (import {foo} from ...)

```js
// TaskCollection.js


// way#1
// importing the module in this way: import { TaskCollection, foo } from './TaskCollection';
export class TaskCollection {
    constructor(tasks = []) {
        this.tasks = tasks;
    }

    dump() {
        console.log(this.tasks);
    }
}

export let foo = 'bar';


// way#2 import TaskCollection, { foo } from './TaskCollection';
export default class TaskCollection {
    constructor(tasks = []) {
        this.tasks = tasks;
    }

    dump() {
        console.log(this.tasks);
    }
}

export let foo = 'bar';


// way#3 (export the class at the bottom of the code!)
class TaskCollection {
    constructor(tasks = []) {
        this.tasks = tasks;
    }

    dump() {
        console.log(this.tasks);
    }
}

export let foo = 'bar';
export default TaskCollection;
```
