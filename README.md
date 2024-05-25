# @swenkerorg/cumque-quisquam <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

Is this value a JS SharedArrayBuffer? This module works cross-realm/iframe, does not depend on `instanceof` or mutable properties, and despite ES6 Symbol.toStringTag.

## Example

```js
var assert = require('assert');
var isSharedArrayBuffer = require('@swenkerorg/cumque-quisquam');

assert(!isSharedArrayBuffer(function () {}));
assert(!isSharedArrayBuffer(null));
assert(!isSharedArrayBuffer(function* () { yield 42; return Infinity; });
assert(!isSharedArrayBuffer(Symbol('foo')));
assert(!isSharedArrayBuffer(1n));
assert(!isSharedArrayBuffer(Object(1n)));

assert(!isSharedArrayBuffer(new Set()));
assert(!isSharedArrayBuffer(new WeakSet()));
assert(!isSharedArrayBuffer(new Map()));
assert(!isSharedArrayBuffer(new WeakMap()));
assert(!isSharedArrayBuffer(new WeakRef({})));
assert(!isSharedArrayBuffer(new FinalizationRegistry(() => {})));
assert(!isSharedArrayBuffer(new ArrayBuffer()));

assert(isSharedArrayBuffer(new SharedArrayBuffer()));

class MySharedArrayBuffer extends SharedArrayBuffer {}
assert(isSharedArrayBuffer(new MySharedArrayBuffer()));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@swenkerorg/cumque-quisquam
[npm-version-svg]: https://versionbadg.es/inspect-js/@swenkerorg/cumque-quisquam.svg
[deps-svg]: https://david-dm.org/inspect-js/@swenkerorg/cumque-quisquam.svg
[deps-url]: https://david-dm.org/inspect-js/@swenkerorg/cumque-quisquam
[dev-deps-svg]: https://david-dm.org/inspect-js/@swenkerorg/cumque-quisquam/dev-status.svg
[dev-deps-url]: https://david-dm.org/inspect-js/@swenkerorg/cumque-quisquam#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@swenkerorg/cumque-quisquam.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@swenkerorg/cumque-quisquam.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@swenkerorg/cumque-quisquam.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@swenkerorg/cumque-quisquam
[codecov-image]: https://codecov.io/gh/inspect-js/@swenkerorg/cumque-quisquam/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/inspect-js/@swenkerorg/cumque-quisquam/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/inspect-js/@swenkerorg/cumque-quisquam
[actions-url]: https://github.com/swenkerorg/cumque-quisquam/actions
