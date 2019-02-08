
# TypeScript Definition/Declaration Files 

If you want to see some examples at the very beginning, [click here](http://www.typescriptlang.org/docs/handbook/declaration-files/templates.html).  

## Library Structures 

### Global Libraries

When looking at the code of a global library, you’ll usually see:

- Top-level `var` statements or function `declarations`
- One or more assignments to `window.someName`
- Assumptions that DOM primitives like `document` or `window` exist

You won’t see:

- Checks for, or usage of, module loaders like require or define
- CommonJS/Node.js-style imports of the form var fs = require("fs");
- Calls to define(...)
- Documentation describing how to require or import the library

Because it’s usually easy to turn a global library into a UMD library, very few popular libraries are still written in the global style. However, libraries that are small and require the DOM (or have no dependencies) may still be global.

### Modular Libraries 

Some libraries only work in a module loader environment. For example, because express only works in Node.js and must be loaded using the CommonJS require function.

ECMAScript 2015 (also known as ES2015, ECMAScript 6, and ES6), CommonJS, and RequireJS have similar notions of importing a module. In JavaScript CommonJS (Node.js), for example, you would write:

```javascript
var fs = require("fs");
```

In TypeScript or ES6, the import keyword serves the same purpose:

```javascript
import fs = require("fs");
```

You’ll typically see modular libraries include one of these lines in their documentation:

```javascript
var someLib = require('someLib');
```

or 

```javascript
define(..., ['someLib'], function(someLib) {

});
```

Modular libraries will typically have at least some of the following:

- Unconditional calls to `require` or `define`
- Declarations `like import * as a from 'b';` or `export c;`
- Assignments to `exports` or `module.exports`

They will rarely have:

- Assignments to properties of `window` or `global`

#### UMD

A UMD module is one that can either be used as module (through an import), or as a global (when run in an environment without a module loader).

[UMD modules](https://github.com/umdjs/umd) check for the existence of a module loader environment. This is an easy-to-spot pattern that looks something like this:

```javascript
(function (root, factory) {
    if (typeof define === "function" && define.amd) {
        define(["libName"], factory);
    } else if (typeof module === "object" && module.exports) {
        module.exports = factory(require("libName"));
    } else {
        root.returnExports = factory(root.libName);
    }
}(this, function (b) { .....
```

If you see tests for typeof define, typeof window, or typeof module in the code of a library, especially at the top of the file, it’s almost always a UMD library. Documentation for UMD libraries will also often demonstrate a “Using in Node.js” example showing require, and a “Using in the browser” example showing using a <script> tag to load the script.