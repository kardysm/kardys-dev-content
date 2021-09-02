+++
author = "Michał Kardyś"
title = "Automation for free"
date = "2020-04-25"
tags = ["n8n","automation"]
categories = ["automation", "app"]

+++
What is more useful for developer than automation?

Some time ago I was digging through _Product Hunt_ (great for discovering new projects with potential!). I've spot a service with enigmatic name - _**n8n**_.
<!--more-->

It turned out to be one of most valuable projects. What's the service about?

I've opened its description. I saw a screenshot. A familiar app! 

Not excatly one I knew, but quite similar. What was it?

In a blink of an eye I knew. Functions like that are built into services in company I currently work for. **Automation**!

What do I mean? 

**It's about moving data from one place to another - via software.** 
Or notifications when something happens. 
In short: it's about schemes like: "when X happend, run Y". Where X and Y are pretty broad terms.

At the moment n8n has plenty of integrations. 

### Who is it for?

Definitely **for developers**. It's self-hosted solution, its' focus is put on services used in development. 

Which?

Examples are: 

* _GitHub_, 
* _AWS_, 
* or just simply _Cron_. 

What's more it has _Functions_, bringing a little bit of serverless feeling into the app. 

Additionaly, **it's kind of open source**. "Kind of" because it has restrictions on commercial use. Besides that, you can use it, view the code and modify it. You can check out yourself how is it made!

While it has services used mostly by dev, n8n has more to offer. It integrates with mailing services like _ActiveCampaign_ or _Mailchimp_.

Or if you need to react on payments, it's built in nodes for PayPal and Stripe. 

These are of course just examples and more and more connected services are added over time.

### What are advantages? 

* It's free (for self-use or inside a company).
* It allows to create complex data paths. 
* You have full control over data flow - app is run on your server
* You can run it using Docker - 1 command and it's set up and running
* It has clean GUI

### Any disadvantages?

* Well, app is run on your server. You have to take care of your hosting.
* Is relatively new technology, its' development is ongoing

### What is it built with?

TypeScript is the language. Additionaly, code is structured into monorepo using lerna workspace manager. Why is TS good here? 

It allows to build maintainable app, typed, without sacrificing its flexibility. Less errors plus flexibility of JavaScript. 

TypeScript's dynamic type checking compares exact data structures and not particular interface being implemented. 

If type expected and type passed have same structure despite being of different type (or one being object literal) you can still use it. 

### Where can you find the tool?

[n8n.io](https://n8n.io)

