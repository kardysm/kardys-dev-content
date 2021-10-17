+++
author = "Michał Kardyś"
title = "More secure TypeScript code - easily"
date = "2021-10-17"
tags = ["typescript","javascript"]
categories = ["typescript","frontend"]

+++

How to secure JS object returned by API as a correct Typescript type?

TS type predicate function helps here. (and it's not the only way)
<!--more-->

## Predicate function

First, let's check the predicate function:

```typescript
  type MyType = {type: 'MY_TYPE'}
    
  function isMyType(value: unknown): value is MyType {
    return value?.type === 'MY_TYPE';
  }
```

How to use it?

```typescript
  const someVal: unknown;

  if(isMyType(someVal)){
    const result: MyType = someVal
  }
```

This check will work, because: 

* TS now knows that condition 
* isMyType passes MyType items

## Want event more secure way? Use asserts

Asserts come with help:
```typescript
  function assertIsMyType(value: any): assert value is MyType {
    if(value?.type !== 'MY_TYPE'){
      throw new AssertionError('Not MyType');
    }
  }

  assertIsMyType(someVal);
  const result: MyType = someVal
```
(see no `if` condition here?)

## Why is it more secure?

Instead of a simple bool value return, assertions throws an error when the condition doesn't pass.

It's a **fail fast** approach that will notify you as soon the function fails to validate type. Besides, you write less 'if'. Code is more straightforward


* * * 

* [More on predicates:
https://www.typescriptlang.org/docs/handbook/advanced-types.html#using-type-predicates](https://www.typescriptlang.org/docs/handbook/advanced-types.html#using-type-predicates)
* [More on assertions:
https://www.typescriptlang.org/docs/handbook/release-notes/typescript-3-7.html#assertion-functions](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-3-7.html#assertion-functions)
