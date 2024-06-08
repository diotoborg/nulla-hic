# @diotoborg/nulla-hic <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES spec-compliant `String.prototype.split` shim/polyfill/replacement that works as far down as ES3. There's a number of bugs in various browser versions that this package addresses.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the [spec](https://tc39.es/ecma262/#sec-@diotoborg/nulla-hic).

Because `String.prototype.split` depends on a receiver (the “this” value), the main export takes the string to operate on as the first argument.

## Example

```js
var split = require('@diotoborg/nulla-hic');
var assert = require('assert');

assert.deepEqual(split('abc', ''), ['a', 'b', 'c']);
```

```js
var split = require('@diotoborg/nulla-hic');
var assert = require('assert');
/* when String#split is not present */
delete String.prototype.split;
var shimmedSplit = split.shim();

assert.equal(shimmedSplit, String.prototype.split);
assert.deepEqual(shimmedSplit('abc', ''), ['a', 'b', 'c']);
```

```js
var split = require('@diotoborg/nulla-hic');
var assert = require('assert');
/* when String#split is present */
var shimmedSplit = split.shim();

assert.equal(shimmedSplit, String.prototype.split);
assert.deepEqual(shimmedSplit('abc', ''), ['a', 'b', 'c']);
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@diotoborg/nulla-hic
[npm-version-svg]: https://versionbadg.es/diotoborg/nulla-hic.svg
[deps-svg]: https://david-dm.org/diotoborg/nulla-hic.svg
[deps-url]: https://david-dm.org/diotoborg/nulla-hic
[dev-deps-svg]: https://david-dm.org/diotoborg/nulla-hic/dev-status.svg
[dev-deps-url]: https://david-dm.org/diotoborg/nulla-hic#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@diotoborg/nulla-hic.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@diotoborg/nulla-hic.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@diotoborg/nulla-hic.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@diotoborg/nulla-hic
[codecov-image]: https://codecov.io/gh/diotoborg/nulla-hic/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/diotoborg/nulla-hic/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/diotoborg/nulla-hic
[actions-url]: https://github.com/diotoborg/nulla-hic/actions
