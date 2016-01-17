# worker loader for webpack with static path

Forked from https://github.com/webpack/worker-loader

Differences:
This loader will add the path of your static files folder when loading the worker js file

## Usage

[Documentation: Using loaders](http://webpack.github.io/docs/using-loaders.html)

Import the worker file:

``` javascript
// main.js
var MyWorker = require("worker-static-loader?{'staticPath':'##PATH_TO_STATIC_FOLDER##'}!./file.js");

var worker = new MyWorker();
worker.postMessage({a: 1});
worker.onmessage = function(event) {...};
worker.addEventListener("message", function(event) {...});
```

The worker file can import dependencies just like any other file:

``` javascript
// file.js
var _ = require('lodash')

var o = {foo: 'foo'}

_.has(o, 'foo') // true
```

You can even use ES6 modules if you have the babel-loader configured:

``` javascript
// file.js
import _ from 'lodash'

let o = {foo: 'foo'}

_.has(o, 'foo') // true
```

## License

MIT (http://www.opensource.org/licenses/mit-license.php)
