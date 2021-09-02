+++
author = "Michał Kardyś"
title = "Learning React - hooks or classes"
date = "2020-04-17"
tags = [
    "react.js",
    "reactjs",
    "react",
    "frontend",
    "front end",
    "developer"
]
categories = [
    "development",
    "react",
]
+++

React exposes 2 general types of writing components. First - older is **classes**. Newer one - **functional with hooks**. Which is better?
<!--more-->

Do you want to learn some frontend? 

If you choose React, you could have little dilemma before starting, one simple question. 

## Should you start with the 'old' react first (components), or should I head straight to hooks?

Basically, it depends. Whatever suits you most is generally better to start with.
           
Both, class and functional, are working; none is going to be deprecated anytime soon.
           
Class components do need more code. On the other side hooks' overuse can quickly lead to messy code.
           
Functional components with hooks are trending right now, so probably you'll see fresher patterns in articles/tutorials

## Okay, but, if you go class route, will the knowledge still be usable later on - when transitioning to hooks? Would you waste time learning classes?

Both styles are generally swappable. It'd be helpful to know both for advanced cases.

Additionally, vast amount of code has been written in 'old style'. If you want to (learn from or) modify legacy code - class way is probably better. 

Classes have advantage of lifecycle methods. Check out this tweet of Dan Abramov - redux framework maker and react contributor: https://r.kardys.dev/jU2

Functional components are simpler. On the other hand you'd have to code lifecycles as custom hooks instead if you need one.

Here's example of class and functional with state hook. These are basically equal:

Class component: 
```class SomeComponent extends React.Component {
  state = {
    //initialState
    elementName: 'div element'

  }

  changeElementName = (newElementName) {
    this.setState({elementName: newElementName})
  }

  render () {
    return <div onClick={()=>{this.changeElementName('something')}}> {this.state.elementName} is rendered</div>
  }
}
```

Functional component with hook
```
const SomeComponent = (props) => {
    const [elementName, changeElementName] = React.useState('div element');
    
    return <div onClick={()=>{changeElementName('something')}}> {elementName} is rendered</div>
}
``` 

If you are beginning your developer path - learning functional way should be easier for you.

Otherwise, pick whatever suit you most.  