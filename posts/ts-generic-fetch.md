+++
title = "Fetch better than built-in?"
description = "How to easily enhance your fetch typing in TS?"
tags = ["tools","dev","frontend"]
date = "2021-07-13"
author = "Michał Kardyś"
categories = ["typescript", "frontend", "npm"]
+++

# Do you fetch your data?

Do you use `fetch` in your projects?

I do. 

But until couple days ago, I didn't think about return value of fetch. 

During discussion (in a course on frontend architecture) this issue was mentioned by one of the mentors. 

## Built-in fetch returns `Promise<any>`

Why didn't anybody use generics for this?

I decided to save myself (and others) some time and post the improved fetch as npm package

![typescript-fetch-before-and-after-applying-improved-typing](/ts-generic-fetch/typescript-fetch-before-and-after-applying-improved-typing.jpg)

New typings enhance fetch, so you can use `fetch<ExpectedReturnType>('fetch-as-usual')`

## Get a package

If you need improved fetch functionality either copy snippet below or install little npm package and just import it at the top of your app 

```
yarn add --dev ts-generic-fetch
// or
npm install --save-dev ts-generic-fetch
```

## Whole package looks like this
This little snippet improves fetch function typing:

```typescript
export {}

declare global {
  interface TypedResponse<ReturnData> extends Response {
    json() : ReturnData extends {} ? Promise<ReturnData> : ReturnType<Response["json"]>
    text() : ReturnData extends string ? Promise<ReturnData> : ReturnType<Response["text"]>
  }
  function fetch<T>(input: RequestInfo, init?: RequestInit): Promise<TypedResponse<T>>;
}
```
