+++
title = "Select your date format with care"
tags = ["browser", "safari", "frontend", "webapp"]
date = "2020-06-13"
author = "Michał Kardyś"
categories = ["programming"]
+++ 
Do you support only the most modern browsers like Chrome, Firefox, Brave or you have to support variety of them? If you have to support browsers like Safari, be careful when dealing with date formats. Here's why. 
<!--more-->
### At first everything worked perfectly

There was one legacy app. It was communicating with backend, sometimes getting dates. In couple formats. It could get `YYYY-MM-DD` or `YYYY-MM` or hourly `YYYY-MM-DD hh:mm:ss`. It had to be working with at least Chrome, Firefox and Safari. Everything worked perfectly. 

Dates were parsed properly - result was returned. Nobody complained. 

The problem was legacy app was built in hurry. Without any multibrowser testing - at first it had to work on Chrome; while it's  one of the most developer friendly browsers it forgives a lot. Forgives and works around standards. 

So, as I said. Date's were parsed right. Just till one day...

### Not rendering?

Days were passing, everything is fine. App's users base are growing. While Chrome is most popular browser till date, it's not the only one. There are various niche and non-niche applications, like... Safari. The day has to come. Somebody has used Safari. Why? It doesn't matter. Browser was supported. 

Many things were right. Many but this one. **The component's rendering relied on timestamp made of date fetched from backend.** 

A ticket came about the bug - component's not loading on Safari. What's going on? 

At first nobody knew. When scope is set to date + hours it just didn't pop. After couple checks: component was rendered right with similar setting - date without hours. It just didn't show up in this one particular case. 

One, yet important. As it allowed users to get more detailed data. 

- At first (routine) - connection check with backend was needed. It was correct. 
- Request was sent properly. 
- Response came - `200`. 

* Payload - as always, correct. Date have the same format all the time, no matter the details chosen. Aha! So it was filtered on frontend.  

So, digging in the code was next step. What's going on? 

Script seemed to work properly, yet when it stumbled upon `new Date(dateString)`, Invalid date was returned on Safari. Why? 

### Let's ask uncle Google

So, after tapping problem into search engine, couple interesting results have popped.  

Among these was correct solution which I happily implemented: `new Date(...dateString.split(/[^0-9]/))`. (new Date can be invoked with one date string or couple arguments which are: year, month, day, hour, etc.)

**Safari (and IE) is expecting `YYYY-MM-DDThh:mm:ss` instead of `YYYY-MM-DD hh:mm:ss`. Little nuance which flipped component over.** 

Couple seconds later, I've checked it. 

- Safari - correct,
- Chrome - correct,
- Firefox - correct.



I thought it was the end, was it?

### 2nd round

Not so fast. This bug was done. I've commented why it happened, I didn't dig deeper then. But after couple hours another bug came. Table with records was showing "*Invalid date*". 

Okay, I've taken this. I suspected it to be similar to previous. 

I've checked response from backend.

On first glance it was correct `2018-07-23T14:00:44.300+0000`. There was infamous `T` in datestring. What was wrong, then? 

**Few tries later - the problem happened to `+0000` - timezone**. As backend was always returning UTC time (+0), I cut it off. 

Check and done.



But timezone in Safari has bugged me. Is it always expecting no timezone? 

It would be irrational. I've decided to dig deeper. 

After a little bit of searching I decided to check ISO format. How does it look like, exactly?



First MDN, later on https://www.w3.org/TR/NOTE-datetime - it was the answer. Safari is expecting either `Z` or `+XX:XX` not `+0000`. **ISO standard in Safari is implemented as w3 said; no more dev-friendly way, no less.** As often - devil lies in details. 



Have you had any problems with date in your web apps? Tell me about them :) 