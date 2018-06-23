# Beginner's Guide

## Install TypeScript

```javascript
npm i typescript -g
tsc -v // Version 2.9.2
```

## Transpile & watch

```javascript
tsc index.ts
tsc --outFile file.js file.ts
tsc @args.txt // Insert command line options and files from a file
tsc -w --out bundle.js index.ts // out DEPRECATED. Use --outFile instead
tsc -w --outFile bundle.js index.ts
```

### tsc --lib

```javascript
 'es5' 'es6' 'es2015' 'es7' 'es2016' 'es2017'
 'es2018' 'esnext' 'dom' 'dom.iterable' 'webworker'
 'scripthost' 'es2015.core' 'es2015.collection'
 'es2015.generator' 'es2015.iterable' 'es2015.promise'
 'es2015.proxy' 'es2015.reflect' 'es2015.symbol'
 'es2015.symbol.wellknown' 'es2016.array.include'
 'es2017.object' 'es2017.sharedmemory' 'es2017.string'
 'es2017.intl' 'es2017.typedarrays' 'es2018.intl'
 'es2018.promise' 'es2018.regexp' 'esnext.array'
 'esnext.asynciterable'
```

## Create tsconfig.json

```javascript
tsc --init
```