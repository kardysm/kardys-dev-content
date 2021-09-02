+++
title = "Less bugs in JavaScript using computed properties."
tags = ["javascript","js","web dev"]
date = "2020-05-26"
author = "Michał Kardyś"
categories = ["programming"]
+++

### What is computed property?

Computed property is feature introduced in ES6. The syntax allows to initialize object using variable's value as a property name in newly created object. 

Instead of<!--more-->:
```javascript
var prop = 'customName'; 
var x = {}; 
x[prop] = 'customValue';
```

you can create object like this: 
```javascript
const prop = 'customName'; 
const x = {
  [prop]: 'customValue'
};
```

New syntax not only simplifies the code, but it has ability to reduce number of bugs. 

### How computed properties will reduce number of bugs in my code?

1. **Keeping things DRY with single source of truth.** 

   Without computed props you'd create object with given prop in one place. And refer to it in another. But both places would keep their names as separate strings. Don't Repeat Yourself (*DRY*) in action

   Let's assume you have:
   ```javascript
   const obj = {
     customProperty: true
   }
   
   function getPropertyFromObj(){
     return obj.customProperty; 
     // or 
     // return obj['customProperty'];
   }
   ```

   What happens if you'd want to change `customProperty` to `anotherProp`? 

   You have to change it in both places - in `obj` and inside `getPropertyFromObj`. 

   So, how will computed properties help here? Let's see another example: 
   ``` javascript
   const PROP = 'customProperty';
   
   const obj = {
     [PROP]: true
   }
   
   function getPropertyFromObj(){
     return obj[PROP];
   }
   ```

   When you need `customProperty` to become `anotherProp`, you just swap it inside `PROP`. In one place. Pretty convenient and simple. 

2. **Build objects dynamically** 

   With computed properties creation of new objects is clearer now. Here's another example:
   ```javascript
   const FOO = 'foo';
   const BAR = 'bar';
   
   const x = {
     [FOO]: 'firstKey',
     [BAR]: 'secondKey'
   };
   
   function shallowCopyWithUpsert(key, val){
     return {
       ...x, //spread x, so new obj has the same properties
       [key]: val // add new key or override existing
     }
   };
   
   alert(shallowCopyWithUpsert(FOO, 'replacedKey'));
   // x is now {'foo': 'replacedKey', 'bar': 'secondKey'}
   
   alert(shallowCopyWithUpsert('nextProp', 'nextVal'));
   // x is now {'foo': 'firstKey', 'bar': 'secondKey': 'nextProp': 'nextVal'}
   ```

   Instead of couple operations and helper variable, now you have ability here to make instant return without loosing readability. 

   Uppercase FOO and BAR are just naming conventions, indicators that these are immutable constants. 

### Do you use computed properties often? What else do you use these for? 

