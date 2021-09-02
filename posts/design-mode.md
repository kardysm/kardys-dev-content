+++
title = "Editable website - quickly adjust web design or make an editor"
tags = ["web design","web dev", "api"]
date = "2020-05-28"
author = "Michał Kardyś"
categories = ["web"]
+++

There's useful propery built in modern browsers to adjust your **designs faster**. Which one? 

If you open your console and write following command, magic happens.<!--more--> 
```javascript
document.designMode="on"
```

### What's design mode?

With the flag turned on, given website becomes editable; document becomes rich-text editor. You can add text or remove it, programatically or manually. 

There's also alternative, `contentEditable`. 

### What's the difference between designMode and contentEditable? 

While designMode works for whole document, contentEditable is for single element. Useful when you need text editor within your app.

```javascript
document.contentEditable=true
``` 

What's more Web API allows to call `execCommand` to programatically copy, cut, paste, etc. if either of the flags above is turned on. 

### How to work with `execCommand`? 
 
 It's best to check MDN as it's great source of programming knowledge. Check out links below.  

More at:
 
- https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Editable_content/Rich-Text_Editing_in_Mozilla
- https://developer.mozilla.org/en-US/docs/Web/API/Document/designMode
- https://developer.mozilla.org/en-US/docs/Web/API/Document/execCommand