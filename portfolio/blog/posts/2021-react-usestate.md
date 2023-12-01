---
title: "React: useState, useEffect and Custom Hooks"
subtitle: "Simplify React Projects with Efficient State Management and Effects"
date: "2021-09-07"
---

## Introduction
React is a powerful JavaScript library for building user interfaces. In this guide, we'll explore three fundamental aspects of React: `useState`, `useEffect`, and custom hooks. These concepts are crucial for managing state and side effects in functional components.




## What are Hooks

React Hooks are simple JavaScript functions that we can use to isolate the reusable part from a functional component. Hooks can be stateful and can manage side-effects.

React provides a bunch of standard in-built hooks. Here are some popular ones:

- **useState**: To manage states. Returns a stateful value and an updater function to update it.
- **useEffect**: To manage side-effects like API calls, subscriptions, timers, mutations, and more.
- **useContext**: To return the current value for a context.


 Please notice that each of these hook names start with use. Yes, this is a standard practice to identify a hook in the React codebase quickly.


## useState Hook

 It will hook/stick to the first initialized value until its state is updated

The `useState` hook is used to manage state within functional components. It allows you to add stateful behavior to your components without converting them into class components. Here's a basic example:

```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}
```

## useEffect Hook
useEffect is a React Hook that lets you synchronize a component with an external system.

#### Synchronizing with Effects 
- Some components need to synchronize with external systems. For example, you might want to control a non-React component based on the React state, set up a server connection, or send an analytics log when a component appears on the screen. Effects let you run some code after rendering so that you can synchronize your component with some system outside of React.

Function inside is guarded, and called only once at first render, not in subsequent renders. 

General Syntax :  useEffect( callback, [] ).
The useEffect hook is used to handle side effects in functional components. Side effects can include data fetching, DOM manipulation, and more.

- **Second parameter []** is an optional array that specifies the dependencies for the effect. It controls when the effect runs. An empty dependency array ([]) means the effect runs once


#### Simple Example
![useEffect](/images/useEffect.png)

## Custom Hooks
Hooks are reusable functions.

When you have component logic that needs to be used by multiple components, we can extract that logic to a custom Hook.

Custom Hooks start with "use". Example: useFetch


#### Example
Here's a basic example of building a custom hook for handling dark mode:

```jsx
Copy code
import { useState } from 'react';

function useDarkMode() {
  const [isDarkMode, setIsDarkMode] = useState(false);

  const toggleDarkMode = () => {
    setIsDarkMode(!isDarkMode);
  };

  return [isDarkMode, toggleDarkMode];
}
```

## Conclusion

In this guide, we covered the essential React hooks: useState and useEffect. 

These hooks empower functional components with state management and side effect capabilities. Additionally, we explored the concept of custom hooks, which allow you to encapsulate and reuse logic efficiently.

