+++
title = "Why software development physically hurts?"
tags = ["software design", "quality", "architecture"]
date = "2020-05-12"
author = "Michał Kardyś"
categories = ["quality","architecture"]
+++
You might think software is just virtual. There's physical world and the "not real". Yet, there's connection between two. What's more - developing low quality software hurt just as much as tons of crap-like products, mass manufactured. 
<!--more-->

I'm not saying bad applications are pure evil. I'm saying the less effective thing you build - the more it hits you, your relatives, friends and others. How so? 

### It's not that virtual

Most people think that computers and separate things from real world. Programmer just builds non-existent applications (okay, maybe robots are different, as we can see these); something existing only inside internet and computer screens are a barrier between unreal and real.

Is it true? Not really.  

While you can't physically hold desktop icon in your hands (well, VR and haptic feedback systems help here) or you aren't feeling movement while changing pages or websites, **software affects us - physically**. Positively and negatively. How?

### Positive side of software

Well, you and me can test an idea in safe place. We build things quickly - really low cost comparing to physical products. Couple decades ago you'd have to burn nice sum of money if you were to build good looking (and working) physical product. Not saying about reaching people via TV, radio or newspapers. 

Now? 

Nowadays you can move from idea to minimally working product in couple hours - day. Reaching potential customers? Right groups, Twitter, Instagram - they're all here. 

**Speed of light** compared to pre-internet times. 

You build fast and most resources you waste is most often your time. Without having to buy physical products. Without even leaving your home. 

Sounds good?

We build tons of new apps, libs and framework. Are you working on frontend or anyhow related to JS world. It's said that new framework or library is being built everyday. How many of these you know? How many of these are really useful? Good's that we have plentiful to choose from. 

And other side of this haste and plenty?

### The dark side

Piles of thrash. First, it starts with virtual garbages. Front doors of services like *github* and *npm* are cool. Most popular projects. Used by thousands or millions. Many of these open sourced. 

Knowledge and actual software - it's all there. 

Do you want to learn better software design on examples? Look through Linux source code.

Need library or framework to help you with your JS project? 

*React*, *Vue*, *Angular*? Or maybe smaller helpers like *ramda* or *lodash*. Fetch and use. 

But, the further you go, you meet stranger and stranger creatures. Projects laying there; unmaintained; forgotten. Yet still taking space. 

Virtual garbage is just **tip of an iceberg**. If it's just once written; it doesn't actively accumulate 'toxins'. It's just waste of disks. Wasteful, yet often necessary. For authors it's helpful as it probably aided them, boosted their learning; or just allowed to test an idea. 

There's something else, worse than just taken bits on servers.

Let's look how today's software is running. Often there's business need to build a feature. The best would be if it's on deployed today. This leads to pressure. Just enough pressure for production team - nothing happens. Especially if they have experience behind. 

They often intuitively know what's better and how to **leverage the need vs quality** during software building process. Not perfect (as nobody is perfect) but good enough; with minimal *technical debt*.

Additionally, they clean up after themselves. Ongoing refactoring is the thing. 

**Yet, how often it happens that a website or an app organises next Apollo rocket launch on your computer?**

And it's not rocket science. It's just an app. CRM, mail or maybe something fancier; yet still, just an app. 

It's poorly written (not saying about optimisations or QA process), yet many people are using it - cursing the creators every minute they have to use it. 

It might be useful, from business perspective but we all loose from it. 

**And looses are beyond virtual; these break the barrier and step into our physical, real world**. How? 

### The physical side 

So, how does bad (poorly written) software affect our world? 

* First of all, it takes more time to use it. Our **time is precious, worth more than money** (you can earn money yet you have finite amount of days living). Every second counts as it does accumulate over time. It's not purely UX, but also developers' concern to build apps not lagging behind.

* Next, less effective code leads to increased power usage. **Increased power usage means not only higher bills**. More electricity equals increased fuel waste (we aren't that green in terms of energy). I'm not saying one app will destroy environment; think about hundrends of them. Add compute power-hungry build tools. Multiply by people working on these apps. And end users. 

  Not only software scales but energy footprints as well.

  Let's check the extreme - how much energy does Bitcoin take? 

  At the time of writing it is around 70TWh per year - similar to Colombia
  I've checked here: https://digiconomist.net/bitcoin-energy-consumption

* Beyond energy, **bad software hurts the hardware**. The more intensive computations are, the sooner you have to replace your computer. Processors and disks have their lifetime and won't live forever. The more components are used the faster these wear out. Like clothes or anything. 

  So, the more bad software you use, the sooner you have to pay for new software. 

  It costs not only you but materials aren't taken out of thin air. Old, not working computer is waste. Production process generates waste. 

These are just 3 examples of how poorly written software affects us physically. But what to do instead?

### To sum up

Cpt obvious says: write better software. Okay, but how? 

1. **Ideal code is no code at all** (as these don't have bugs). So practically, the less code you generate, the better. 
   I'm not saying less worthy code, but don't bruteforce things when you can write the same in a more elegant manner. 

2. TEST IT. You might have QA's in your company, but the person most responsible for the code is developer. Set up **metrics** and set up **tests**. It helps produce better outcome and prevent bugs. 

3. **Think before acting**. What's new feature to be user for? Why is it to be written? Isn't there anything like that already? 

 **Do you agree? Let's talk**