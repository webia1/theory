# TypeScript Cookbook

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [TypeScript Cookbook](#typescript-cookbook)
  - [Other Ressources](#other-ressources)
  - [Initialize TS](#initialize-ts)
  - [Compiler Options](#compiler-options)
    - [Some Checks](#some-checks)
  - [Use same name for Class and Interface](#use-same-name-for-class-and-interface)
  - [Type Definitions](#type-definitions)
    - [An Array of a certain type at least with e.g. 2 elements](#an-array-of-a-certain-type-at-least-with-eg-2-elements)

<!-- /code_chunk_output -->

## Other Ressources

- [Release Notes](https://www.typescriptlang.org/docs/handbook/release-notes/overview.html)

## Initialize TS

```bash
tsc --init
```

## Compiler Options

### Some Checks

```json
{
  "compilerOptions": {
    "noImplicitAny": true,
    "strictNullChecks": true
  }
}
```

## Use same name for Class and Interface

You don't have to repeat prop-names within the class:

```javascript
interface SomeClass {
  propOne: string;
  propTwo: number;
}

class SomeClass {
  constructor(one: string, two: number) {
    this.propOne = one;
    this.propTwo = two;
  }
}
```

## Type Definitions

### An Array of a certain type at least with e.g. 2 elements

[>> Source StackOverflow](https://stackoverflow.com/questions/57117317/type-definition-an-array-of-a-certain-type-at-least-with-e-g-2-elements)

See _Rest Elements in tuple types_ here:
https://www.typescriptlang.org/docs/handbook/release-notes/overview.html#rest-elements-in-tuple-types

```javascript
let foo: [Foo, Foo, ...Foo[]];
```

And see additionally _User-defined type guards_ here:
https://www.typescriptlang.org/docs/handbook/advanced-types.html#user-defined-type-guards

To define a type guard, we simply need to define a function whose return type is
a type predicate:

```javascript
function isAtLeastTwoFoos(x: Foo[]): x is [Foo, Foo, ...Foo[]] {
  return x.length >= 2;
}

if (isAtLeastTwoFoos(fooArray)) {
  foo = fooArray; // okay
}
```