+++
title = "Setup external modules with React Context"
description = "The pattern helpful for managing external modules in React. Using context to manage shared code"
tags = ["react","dev","dependecies"]
date = "2021-04-20"
author = "Michał Kardyś"
categories = ["react"]
+++

A pattern that is helpful when you use external modules in your app.

<!--more-->

Some time ago Dan Abramov posted this tweet:

{{< tweet 1363134687250636800 >}}

```
<Context.Provider value={<RenderedComponent />}>
  <Something />
</Context.Provider>
```

This pattern is neither necessary nor common, yet it is useful at certain times.

## What are use cases?

The pattern is helpful when external modules arise. What exactly do I mean by external module?

See, chat. Let's assume you have SPA and you want to add Intercom-like chat to your app.

Should you setup it somewhere down in your render-tree? 

It is an option.

```
FloatingButton.jsx
//...
<Chat
	prop1={prop1}
	flag
	anotherFlag
	/>
	
```

Yet,
## What if you need a change?

* You might need it in 2+ places:
    * under a floating button
    * or when user selects 'help' section
    * so, you instantiate 2 some components 2 times?
* You might want to keep all external configs in one place
    * to have an eye on dependencies
    * to slowly replace all externals with your internal code
    * would looking for all of these usages be simple? It might

...but there's another way

## Setup external component with context

What if instead of:

```
FloatingButton.jsx
//...
<Chat
	prop1={prop1}
	flag
	anotherFlag
	/>
	
HelpSection.jsx
//...
<Chat
	prop1={prop1}
	flag
	anotherFlag
	/>
```

you do:
```
ExternalModules
export const ExternalChatProvider = (props) => <Context.Provider value={<Chat
	prop1={prop1}
	flag
	anotherFlag
	/>}
	{...props}
	/>
export const ExternalChatConsumer = (props) => <Context.Consumer {...props}/>
  
Main
//...
<ExternalChatProvider>
	<SPA/>
</ExternalChatProvider>

FloatingButton
//...
<ExternalChatConsumer/>

HelpSection
//...
<ExternalChatConsumer/>

```

It:

* has single point of config
* follows DRY rule
* clearly signals that module is external (read: possibly unsafe)
* rendered once

I've simplified code, but you could:

* add memoization,
* parametrize it,
* etc.

This technique is useful not only for external modules, but for using shared components in general.

A word of caution: do not overuse

* context is additional component,
* it causes jumps in logic and
* it is harder to read app flow with to many contexts.

**How do you manage external components?**
