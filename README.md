# clean-css-promise

[![NPM version](https://img.shields.io/npm/v/clean-css-promise.svg)](https://www.npmjs.com/package/clean-css-promise)
[![Build Status](https://travis-ci.org/shinnn/clean-css-promise.svg?branch=master)](https://travis-ci.org/shinnn/clean-css-promise)
[![Coverage Status](https://img.shields.io/coveralls/shinnn/clean-css-promise.svg)](https://coveralls.io/github/shinnn/clean-css-promise?branch=master)
[![dependencies Status](https://david-dm.org/shinnn/clean-css-promise/status.svg)](https://david-dm.org/shinnn/clean-css-promise)
[![devDependencies Status](https://david-dm.org/shinnn/clean-css-promise/dev-status.svg)](https://david-dm.org/shinnn/clean-css-promise?type=dev)

[clean-css](https://github.com/jakubpawlowicz/clean-css) with the default [Promise](https://developer.mozilla.org/docs/Mozilla/JavaScript_code_modules/Promise.jsm/Promise) interface and some improvements

```javascript
const CleanCssPromise = require('clean-css-promise');

new CleanCssPromise()
.minify('p { margin: 1px 1px 1px 1px; }')
.then(result => console.log(result.styles)) //=> 'p{margin:1px}'
```

## Installation

[Use npm.](https://docs.npmjs.com/cli/install)

```
npm install clean-css-promise
```

## API

```javascript
const CleanCssPromise = require('clean-css-promise');
```

### class CleanCssPromise([*options*])

*options*: `Object` ([clean-css constructor options](https://github.com/jakubpawlowicz/clean-css#constructor-options))  


It has the same API as [clean-css's][clean-css-api], except for:

* `.minify()` method is [promisified](https://promise-nuggets.github.io/articles/07-wrapping-callback-functions.html).
* The error passed to [*onRejected*](https://promisesaplus.com/#point-30) function is modified with [array-to-error](https://github.com/shinnn/array-to-error).

```javascript
const CleanCssPromise = require('clean-css-promise');

new CleanCssPromise({})
.minify('@import /foo;@import /bar;')
.catch(err => {
  console.error(err.message);
  //=> 'Broken @import declaration of "/foo"\nBroken @import declaration of "/bar"'
});
```

## License

Copyright (c) 2015 - 2017 [Shinnosuke Watanabe](https://github.com/shinnn)

Licensed under [the MIT License](./LICENSE).
