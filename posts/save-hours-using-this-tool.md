+++
title = "How to save hours of implementation time?"
tags = ["tool","generator", "documentation", "productivity"]
date = "2020-06-19"
author = "Michał Kardyś"
categories = ["programming"]
+++ 

Code generation gets better and better, so why not to use it? Time of implementing API client in your apps is often huge. And it can be cut off, often totally. Meaning you can save hours of time reimplementing things that have been written on backend. How?
<!--more-->
### Start with contract

Cooperation between server and client start with contract. It's often considered as backend part, some people think it's frontend ownership as it's the client that will use its API, but the truth lies between. It is not backend's nor frontend's part, but both. 

API contract is agreement between two sides and both sides must respect it without changing it freely. If someone would modify API or client, the system would break, hence no one is true owner and it is just ownership of two sides. 



### Next - build an API

Standard part of development - building an API. If you need to communicate between server and browser or, for example, between 2 servers, you need some kind of API to communicate with.

Building is not part of this article. You probably already know how to do it ;) 



### Document it

Devs often ignore necessity of documenting code properly. But in documentation lies its strength. Properly documented API is easier to use. You don't have to ping developer who build endpoints, but you look into documentation and use it as it's written there. 

Simple.

The most common way to document your API is via Swagger and its openAPI specification (https://swagger.io/). It's popular because it's relatively easy to write (or generate) for engineers. Docs are written in JSON or YAML format and based on this you can generate doc pages. 

But we are not there yet.



### Save time with openApi generator

The most time-saving job in this process is next step. Using openApi is not only for reading documentation. You can use it to let your client (be it an app or other server) read the specification, too!

How? 

Tool like openApi generator (https://openapi-generator.tech/#try) does the heavy lifting for you! you take API spec, run generator and voila. Output is a set of ready to use classes, types, and functions - whole API client (with proper typing). **In just one command.**

Something like `openapi-generator generate -i petstore.yaml -g typescript-fetch -o /tmp/test/` will setup whole client for you. 

My mostly used generator is `typescript-fetch` but you can use it for multitude of languages, from Java, through Scala, Typescript to even Python or Ruby. Full list of generators is available here: https://openapi-generator.tech/docs/generators



### Where's the catch?

The generator works as promised on its website, but it's not perfect. Sometimes you have to manually tweak some models.

I remember I had to tweak TypeScript polymorphic models that were specified as `oneOf` or `allOf`. When tweaking the model manually you have to set your script to ignore these models when regenerating them. I can be problem when API often changes and its regenerated autmatically during application build.

While you are reading this, this problem might be fixed though. 



_____

Next thing, specs validators and doc generators can be less restrictive than this code generator. I've stumbled across model that was specified like:

```yaml
...
Something:
	type: object
  properties:
		value:
			description: The value of something
			oneOf:
				- type: string
				- type: array
				- type: number
				- type: object
```



And when I've tried to generate client, an error occured:

```yaml
Errors: 
        -attribute components.schemas.Something.items is missing
```

I was puzzled at the beginning. After digging a while in documentation and eliminating options the problem was:

```yaml
- type: array
	items:
		oneOf:
			- type: string
			- type: number
			- type: boolean
			- type: object
```

Instead of

```
- type: array
```

Validators passed this error, documentation was shown properly, yet generator stopped it.



______

To sum up. If you want to shave off massive amount of time try it: https://openapi-generator.tech/#try

**What do you think of openApi generator? Did you know it? Will it be helpful in your projects?**