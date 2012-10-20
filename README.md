# Autonomy [![Build Status](https://secure.travis-ci.org/clux/autonomy.png)](http://travis-ci.org/clux/autonomy)

Autonomy is a lightweight functional helper library. It is meant to complement an ES5 style with curried helpers, math helpers, curried accessors and higher order looping constructs.

These library is partly inspired by Haskell's [Prelude](http://www.haskell.org/ghc/docs/latest/html/libraries/base/Prelude.html), but its exports are optimized for JavaScript semantics and performance. It does not try to make JavaScript into something it's not.

## Usage
Attach it to the short variable of choice:

```js
var $ = require('autonomy');
```

and get functional:

```javascript
$.id(x) === x;
$.noop(x) === undefined;

[1,3,2].map($.constant(5)); // [5, 5, 5]

[1,2,3,4,3].filter($.elem([1,3])); // [ 1, 3, 3 ]

[1,3,5,-1].some($.notElem([1,2,3,4,5])); // true

$.gcd(10, 15); // 5

[1,2,3,4,5,6].filter($.even); // [ 2, 4, 6 ]

$.range(5); // [ 1, 2, 3, 4, 5 ]

$.zip($.range(5), [1,2], [3,2,5]); // [ [ 1, 1, 3 ], [ 2, 2, 2 ] ]
$.zipWith(op.plus2, [1,1,1], $.range(5)); // [ 2, 3, 4 ]

$.iterate(3, "ha!", function (str) {
  return "ha" + str
}); // [ 'ha!', 'haha!', 'hahaha!' ]

[[1,2], [3,4]].map($.invoke('join','w')); // [ '1w2', '3w4']
```

Read the read the [API](https://github.com/clux/autonomy/blob/master/api.md).
In most cases the [operators](https://github.com/clux/operators) module provides some must have additions to [autonomy]. It's referenced once above as `op`, and you can just do `$.extend($, require('operators'))` to import all the helpers onto autonomy's object.

NB: This modules makes up the core part of the larger utility library: [interlude](https://github.com/clux/interlude). If you find yourself extending with [operators] or [subset] a lot, you should use [interlude] instead (there's also more documentation there).

## Installation

```bash
$ npm install autonomy
```

## Running tests
Install development dependencies

```bash
$ npm install
```

Run the tests

```bash
$ npm test
```

## License
MIT-Licensed. See LICENSE file for details.