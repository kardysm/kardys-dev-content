+++
title = "Singleton-like Context for shared components managent"
description = "Are you handling external modules or shared config in your React projects?"
tags = ["react","dev","context"]
date = "2021-04-21"
author = "Michał Kardyś"
categories = ["react"]
+++

Are you handling external modules or shared config in your React projects?

<!--more-->

React Context, when overused, can become hell. On the other hand, Setting up shared modules/config with Context can be helpful.

## How to handle shared config?

Regular Context is hidden by Provider down the render tree.

What if we... make a singleton?

Single place for your settings is helpful. You have easy go-to place if you need to update your config. Yet, with increasing modularity of your code it becomes harder and harder.

So, should you setup Redux workflow?

If the app is not big/complex Redux is not goto. It's like shooting a pigeon with a cannon. Overkill.

What then?

Single source of truth would be helpful. A singleton.

How to do it?

Let's inverse our context! Let's prevent providers down the tree. Let's...

## Create context singleton

Simplest implementation for singleton-like context:
```
const NOT_INSTANTIATED = 'NOT_INSTANTIATED';

const Context = React.createContext(NOT_INSTANTIATED);

function SingletonContext(props){
  const value = React.useContext(Context)

  if(value === NOT_INSTANTIATED){
    return <Context.Provider {...props}/>
  }
  
  return <React.Fragment {...props}/>
}
```

What happens here?

You create React context with defaul "NOT_INSTATIATED" value. So, if use consume the context and no provider is rendered above - you get the default value.

Next is wrapper.

`SingletonContext` does following:

1. Consumes provider
2. If it hasn't been instatiated earlier create provider
3. Otherwise return Fragment

## Singleton in action

```
const Display = () => {
  const value = React.useContext(Context)
  
  return <div>{value}</div>;
};

const App = () => {
  return <React.Fragment>
    <SingletonContext value={'first'}>
      <SingletonContext value={'second'}>
        <Display/>
      </SingletonContext>
    </SingletonContext>
  </React.Fragment>
}
```

When we create 2 SingletonContext components, the former Context.Provider is created

Result is:
`first` is passed to `Display` consumer

What if we create parallel Provider?

```
const App = () => {
  return <React.Fragment>
    <SingletonContext value={'first'}>
      <SingletonContext value={'second'}>
        <Display/>
      </SingletonContext>
    </SingletonContext>
	
    <SingletonContext value={'separate render tree'}>
      <Display/>
    </SingletonContext>
  </React.Fragment>
}
```

Now we have, as expected, 2 results:

* first
* separate render tree

That why it's not fully singleton (unless you put it in app root).

## Use cases

1. Config shared between many apps
2. Redux singleton (we can render redux provider similar way)
3. Many components loosely scattered
    * each needing a common theme provider or so
    * this way we can 'safeguard provider' and render it if not present

It is, of course, not 'the only right way' to do things.

For external modules you might want [**this method from my previous post**](https://www.kardys.dev/2021/04/external-modules-in-react-context/), too.

**How do you manage your configs?**

See code in action:
[codepen](https://codepen.io/Drak29/pen/gOgBJqO)
