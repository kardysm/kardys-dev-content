+++
author = "Michał Kardyś"
title = "State management - more than 'isLoaded'"
date = "2020-04-19"
tags = ["react","state management", "applications"]
categories = ["react", "development"]
+++

Async state management can be done better than setting flags 'isLoaded' and 'isLoading'. What's better? 
<!--more-->

## Basic flags 

You can start making (not only) React's async state management with flags.

Let's assume you want to load data from backend to your React app. You would want to show placeholders when data is not fetched. What's the simplest way? 

```jsx
const Component = ({isLoaded, data, ...otherProps}) => {
  if (!isLoaded){
    return <Placeholder/>;
  }

  return <DataLoadedView data={data} />;
}
``` 

Convenient? 

Yeah. For simplest use cases. What should you do when you need additional state - during load?

Stuff gets more complicated; less maintainable:

```jsx
const Component = ({isLoading, isLoaded, data, ...otherProps}) => {
  if (isLoading){ 
    return <ProgressBar/>;
  }

  if (!isLoaded){
    return <Placeholder/>;
  }

  return <DataLoadedView data={data} />;
}
``` 

What if you need more states like this?

Component's code will get messy in a blink of an eye.
Each time you want to introduce new component state, additional flag would have to be introduced. 

Convenient? Not at all!

So, how to make it better?

## Enum for the rescue

Our white knight here could be enum. More maintainable, takes less memory.

How so? Let's look at the next example:

 ```jsx
 const STATE = {
         INITIAL: () => <Placeholder/>,
         LOADING: () => <ProgressBar/>,
         LOADED: (data) => <DataLoadedView data={data} />,
         ERROR: () => <ErrorComponent/>,
 };

 const Component = ({loadingStatus, data, ...otherProps}) => {
  return STATE[loadingStatus || 'INITIAL'](data);    
 }
 ```  
I have simplified this example to focus on enum-like state; each status name could be string/symbol constants to avoid typos. 

What if you need another state? Just add it to the 'STATE'.

It's simple like that. 

What do you think of this pattern? 
Do you use something else? 
