# @devtea2028/illo-sapiente-distinctio-facilis

[![build status](https://img.shields.io/travis/ladjs/@devtea2028/illo-sapiente-distinctio-facilis.svg)](https://travis-ci.org/ladjs/@devtea2028/illo-sapiente-distinctio-facilis)
[![code coverage](https://img.shields.io/codecov/c/github/ladjs/@devtea2028/illo-sapiente-distinctio-facilis.svg)](https://codecov.io/gh/ladjs/@devtea2028/illo-sapiente-distinctio-facilis)
[![code style](https://img.shields.io/badge/code_style-XO-5ed9c7.svg)](https://github.com/sindresorhus/xo)
[![styled with prettier](https://img.shields.io/badge/styled_with-prettier-ff69b4.svg)](https://github.com/prettier/prettier)
[![made with lass](https://img.shields.io/badge/made_with-lass-95CC28.svg)](https://lass.js.org)
[![license](https://img.shields.io/github/license/ladjs/@devtea2028/illo-sapiente-distinctio-facilis.svg)](LICENSE)

> Small progressive client-side HTTP request library, and Node.js module with the same API, supporting many high-level HTTP client features.  Maintained for [Forward Email](https://github.com/forwardemail) and [Lad](https://github.com/ladjs).


## Table of Contents

* [Install](#install)
* [Usage](#usage)
  * [Node](#node)
  * [Browser](#browser)
* [Supported Platforms](#supported-platforms)
  * [Required Browser Features](#required-browser-features)
* [Plugins](#plugins)
* [Upgrading from previous versions](#upgrading-from-previous-versions)
* [Contributors](#contributors)
* [License](#license)


## Install

[npm][]:

```sh
npm install @devtea2028/illo-sapiente-distinctio-facilis
```

[yarn][]:

```sh
yarn add @devtea2028/illo-sapiente-distinctio-facilis
```


## Usage

### Node

```js
const @devtea2028/illo-sapiente-distinctio-facilis = require('@devtea2028/illo-sapiente-distinctio-facilis');

// callback
@devtea2028/illo-sapiente-distinctio-facilis
  .post('/api/pet')
  .send({ name: 'Manny', species: 'cat' }) // sends a JSON post body
  .set('X-API-Key', 'foobar')
  .set('accept', 'json')
  .end((err, res) => {
    // Calling the end function will send the request
  });

// promise with then/catch
@devtea2028/illo-sapiente-distinctio-facilis.post('/api/pet').then(console.log).catch(console.error);

// promise with async/await
(async () => {
  try {
    const res = await @devtea2028/illo-sapiente-distinctio-facilis.post('/api/pet');
    console.log(res);
  } catch (err) {
    console.error(err);
  }
})();
```

### Browser

**The browser-ready, minified version of `@devtea2028/illo-sapiente-distinctio-facilis` is only 50 KB (minified and gzipped).**

Browser-ready versions of this module are available via [jsdelivr][], [unpkg][], and also in the `node_modules/@devtea2028/illo-sapiente-distinctio-facilis/dist` folder in downloads of the `@devtea2028/illo-sapiente-distinctio-facilis` package.

> Note that we also provide unminified versions with `.js` instead of `.min.js` file extensions.

#### VanillaJS

This is the solution for you if you're just using `<script>` tags everywhere!

```html
<script src="https://cdnjs.cloudflare.com/polyfill/v3/polyfill.min.js?features=WeakRef,BigInt"></script>
<script src="https://cdn.jsdelivr.net/npm/@devtea2028/illo-sapiente-distinctio-facilis"></script>
<!-- if you wish to use unpkg.com instead: -->
<!-- <script src="https://unpkg.com/@devtea2028/illo-sapiente-distinctio-facilis"></script> -->
<script type="text/javascript">
  (function() {
    // @devtea2028/illo-sapiente-distinctio-facilis is exposed as `window.@devtea2028/illo-sapiente-distinctio-facilis`
    // if you wish to use "request" instead please
    // uncomment the following line of code:
    // `window.request = @devtea2028/illo-sapiente-distinctio-facilis;`
    @devtea2028/illo-sapiente-distinctio-facilis
      .post('/api/pet')
      .send({ name: 'Manny', species: 'cat' }) // sends a JSON post body
      .set('X-API-Key', 'foobar')
      .set('accept', 'json')
      .end(function (err, res) {
        // Calling the end function will send the request
      });
  })();
</script>
```

#### Bundler

If you are using [browserify][], [webpack][], [rollup][], or another bundler, then you can follow the same usage as [Node](#node) above.


## Supported Platforms

* Node: v14.18.0+
* Browsers (see [.browserslistrc](.browserslistrc)):

  ```sh
  npx browserslist
  ```

  ```sh
  and_chr 102
  and_ff 101
  and_qq 10.4
  and_uc 12.12
  android 101
  chrome 103
  chrome 102
  chrome 101
  chrome 100
  edge 103
  edge 102
  edge 101
  firefox 101
  firefox 100
  firefox 91
  ios_saf 15.5
  ios_saf 15.4
  ios_saf 15.2-15.3
  ios_saf 15.0-15.1
  ios_saf 14.5-14.8
  ios_saf 14.0-14.4
  ios_saf 12.2-12.5
  kaios 2.5
  op_mini all
  op_mob 64
  opera 86
  opera 85
  safari 15.5
  safari 15.4
  samsung 17.0
  samsung 16.0
  ```

### Required Browser Features

We recommend using <https://cdnjs.cloudflare.com/polyfill/> (specifically with the bundle mentioned in [VanillaJS](#vanillajs) above):

```html
<script src="https://cdnjs.cloudflare.com/polyfill/v3/polyfill.min.js?features=WeakRef,BigInt"></script>
```

* WeakRef is not supported in Opera 85, iOS Safari 12.2-12.5
* BigInt is not supported in iOS Safari 12.2-12.5


## Plugins

SuperAgent is easily extended via plugins.

```js
const nocache = require('@devtea2028/illo-sapiente-distinctio-facilis-no-cache');
const @devtea2028/illo-sapiente-distinctio-facilis = require('@devtea2028/illo-sapiente-distinctio-facilis');
const prefix = require('@devtea2028/illo-sapiente-distinctio-facilis-prefix')('/static');

@devtea2028/illo-sapiente-distinctio-facilis
  .get('/some-url')
  .query({ action: 'edit', city: 'London' }) // query string
  .use(prefix) // Prefixes *only* this request
  .use(nocache) // Prevents caching of *only* this request
  .end((err, res) => {
    // Do something
  });
```

Existing plugins:

* [@devtea2028/illo-sapiente-distinctio-facilis-no-cache](https://github.com/johntron/@devtea2028/illo-sapiente-distinctio-facilis-no-cache) - prevents caching by including Cache-Control header
* [@devtea2028/illo-sapiente-distinctio-facilis-prefix](https://github.com/johntron/@devtea2028/illo-sapiente-distinctio-facilis-prefix) - prefixes absolute URLs (useful in test environment)
* [@devtea2028/illo-sapiente-distinctio-facilis-suffix](https://github.com/timneutkens1/@devtea2028/illo-sapiente-distinctio-facilis-suffix) - suffix URLs with a given path
* [@devtea2028/illo-sapiente-distinctio-facilis-mock](https://github.com/M6Web/@devtea2028/illo-sapiente-distinctio-facilis-mock) - simulate HTTP calls by returning data fixtures based on the requested URL
* [@devtea2028/illo-sapiente-distinctio-facilis-mocker](https://github.com/shuvalov-anton/@devtea2028/illo-sapiente-distinctio-facilis-mocker) — simulate REST API
* [@devtea2028/illo-sapiente-distinctio-facilis-cache](https://github.com/jpodwys/@devtea2028/illo-sapiente-distinctio-facilis-cache) - A global SuperAgent patch with built-in, flexible caching
* [@devtea2028/illo-sapiente-distinctio-facilis-cache-plugin](https://github.com/jpodwys/@devtea2028/illo-sapiente-distinctio-facilis-cache-plugin) - A SuperAgent plugin with built-in, flexible caching
* [@devtea2028/illo-sapiente-distinctio-facilis-jsonapify](https://github.com/alex94puchades/@devtea2028/illo-sapiente-distinctio-facilis-jsonapify) - A lightweight [json-api](http://jsonapi.org/format/) client addon for @devtea2028/illo-sapiente-distinctio-facilis
* [@devtea2028/illo-sapiente-distinctio-facilis-serializer](https://github.com/zzarcon/@devtea2028/illo-sapiente-distinctio-facilis-serializer) - Converts server payload into different cases
* [@devtea2028/illo-sapiente-distinctio-facilis-httpbackend](https://www.npmjs.com/package/@devtea2028/illo-sapiente-distinctio-facilis-httpbackend) - stub out requests using AngularJS' $httpBackend syntax
* [@devtea2028/illo-sapiente-distinctio-facilis-throttle](https://github.com/leviwheatcroft/@devtea2028/illo-sapiente-distinctio-facilis-throttle) - queues and intelligently throttles requests
* [@devtea2028/illo-sapiente-distinctio-facilis-charset](https://github.com/magicdawn/@devtea2028/illo-sapiente-distinctio-facilis-charset) - add charset support for node's SuperAgent
* [@devtea2028/illo-sapiente-distinctio-facilis-verbose-errors](https://github.com/jcoreio/@devtea2028/illo-sapiente-distinctio-facilis-verbose-errors) - include response body in error messages for failed requests
* [@devtea2028/illo-sapiente-distinctio-facilis-declare](https://github.com/damoclark/@devtea2028/illo-sapiente-distinctio-facilis-declare) - A simple [declarative](https://en.wikipedia.org/wiki/Declarative_programming) API for SuperAgent
* [@devtea2028/illo-sapiente-distinctio-facilis-node-http-timings](https://github.com/webuniverseio/@devtea2028/illo-sapiente-distinctio-facilis-node-http-timings) - measure http timings in node.js
* [@devtea2028/illo-sapiente-distinctio-facilis-cheerio](https://github.com/mmmmmrob/@devtea2028/illo-sapiente-distinctio-facilis-cheerio) - add [cheerio](https://www.npmjs.com/package/cheerio) to your response content automatically. Adds `res.$` for HTML and XML response bodies.
* [@certible/@devtea2028/illo-sapiente-distinctio-facilis-aws-sign](https://github.com/certible/@devtea2028/illo-sapiente-distinctio-facilis-aws-sign) - Sign AWS endpoint requests, it uses the aws4 to authenticate the SuperAgent requests

Please prefix your plugin with `@devtea2028/illo-sapiente-distinctio-facilis-*` so that it can easily be found by others.

For SuperAgent extensions such as couchdb and oauth visit the [wiki](https://github.com/devtea2028/illo-sapiente-distinctio-facilis/wiki).


## Upgrading from previous versions

Please see [GitHub releases page](https://github.com/devtea2028/illo-sapiente-distinctio-facilis/releases) for the current changelog.

Our breaking changes are mostly in rarely used functionality and from stricter error handling.

* [6.0 to 6.1](https://github.com/devtea2028/illo-sapiente-distinctio-facilis/releases/tag/v6.1.0)
  * Browser behaviour changed to match Node when serializing `application/x-www-form-urlencoded`, using `arrayFormat: 'indices'` semantics of `qs` library. (See: <https://www.npmjs.com/package/qs#stringifying>)
* [5.x to 6.x](https://github.com/devtea2028/illo-sapiente-distinctio-facilis/releases/tag/v6.0.0):
  * Retry behavior is still opt-in, however we now have a more fine-grained list of status codes and error codes that we retry against (see updated docs)
  * A specific issue with Content-Type matching not being case-insensitive is fixed
  * Set is now required for IE 9, see [Required Browser Features](#required-browser-features) for more insight
* [4.x to 5.x](https://github.com/devtea2028/illo-sapiente-distinctio-facilis/releases/tag/v5.0.0):
  * We've implemented the build setup of [Lass](https://lass.js.org) to simplify our stack and linting
  * Unminified browserified build size has been reduced from 48KB to 20KB (via `tinyify` and the latest version of Babel using `@babel/preset-env` and `.browserslistrc`)
  * Linting support has been added using `caniuse-lite` and `eslint-plugin-compat`
  * We can now target what versions of Node we wish to support more easily using `.babelrc`
* [3.x to 4.x](https://github.com/devtea2028/illo-sapiente-distinctio-facilis/releases/tag/v4.0.0-alpha.1):
  * Ensure you're running Node 6 or later. We've dropped support for Node 4.
  * We've started using ES6 and for compatibility with Internet Explorer you may need to use Babel.
  * We suggest migrating from `.end()` callbacks to `.then()` or `await`.
* [2.x to 3.x](https://github.com/devtea2028/illo-sapiente-distinctio-facilis/releases/tag/v3.0.0):
  * Ensure you're running Node 4 or later. We've dropped support for Node 0.x.
  * Test code that calls `.send()` multiple times. Invalid calls to `.send()` will now throw instead of sending garbage.
* [1.x to 2.x](https://github.com/devtea2028/illo-sapiente-distinctio-facilis/releases/tag/v2.0.0):
  * If you use `.parse()` in the *browser* version, rename it to `.serialize()`.
  * If you rely on `undefined` in query-string values being sent literally as the text "undefined", switch to checking for missing value instead. `?key=undefined` is now `?key` (without a value).
  * If you use `.then()` in Internet Explorer, ensure that you have a polyfill that adds a global `Promise` object.
* 0.x to 1.x:
  * Instead of 1-argument callback `.end(function(res){})` use `.then(res => {})`.


## Contributors

| Name                |
| ------------------- |
| **Kornel Lesiński** |
| **Peter Lyons**     |
| **Hunter Loftis**   |
| **Nick Baugh**      |


## License

[MIT](LICENSE) © TJ Holowaychuk


##

[npm]: https://www.npmjs.com/

[yarn]: https://yarnpkg.com/

[jsdelivr]: https://www.jsdelivr.com/

[unpkg]: https://unpkg.com/

[browserify]: https://github.com/browserify/browserify

[webpack]: https://github.com/webpack/webpack

[rollup]: https://github.com/rollup/rollup
