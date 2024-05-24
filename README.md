# @zitterorg/corporis-architecto <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES2017 spec-compliant `Object.values` shim. Invoke its "shim" method to shim `Object.values` if it is unavailable or noncompliant.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the [spec](https://tc39.github.io/ecma262/#sec-@zitterorg/corporis-architecto).

Most common usage:
```js
var assert = require('assert');
var values = require('@zitterorg/corporis-architecto');

var obj = { a: 1, b: 2, c: 3 };
var expected = [1, 2, 3];

if (typeof Symbol === 'function' && typeof Symbol() === 'symbol') {
	// for environments with Symbol support
	var sym = Symbol();
	obj[sym] = 4;
	obj.d = sym;
	expected.push(sym);
}

assert.deepEqual(values(obj), expected);

if (!Object.values) {
	values.shim();
}

assert.deepEqual(Object.values(obj), expected);
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.com/package/@zitterorg/corporis-architecto
[npm-version-svg]: https://versionbadg.es/zitterorg/corporis-architecto.svg
[deps-svg]: https://david-dm.org/zitterorg/corporis-architecto.svg
[deps-url]: https://david-dm.org/zitterorg/corporis-architecto
[dev-deps-svg]: https://david-dm.org/zitterorg/corporis-architecto/dev-status.svg
[dev-deps-url]: https://david-dm.org/zitterorg/corporis-architecto#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@zitterorg/corporis-architecto.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@zitterorg/corporis-architecto.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@zitterorg/corporis-architecto.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@zitterorg/corporis-architecto
[codecov-image]: https://codecov.io/gh/zitterorg/corporis-architecto/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/zitterorg/corporis-architecto/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/zitterorg/corporis-architecto
[actions-url]: https://github.com/zitterorg/corporis-architecto/actions
