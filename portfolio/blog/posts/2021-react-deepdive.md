---
title: "React: JSX, Components, and Props"
subtitle: "Learn the fundamentals of the most popular javascript framework"
date: "2021-04-8"
---

## JSX in React

React makes it easy to create HTML elements using JSX, a syntax extension of JavaScript. JSX looks like HTML and compiles into React elements, making it easier to create templates and maintain the markup and logic together.

- It performs optimizations while translating to regular JavaScript.
- It simplifies the creation of templates.
- React uses components to organize UI, avoiding the separation of markup and logic.

JSX is a syntax extension of JavaScript that combines the JavaScript and HTML-like syntax to provide highly functional, reusable markup. It’s used to create DOM elements which are then rendered in the React DOM.

While not required in React, JSX provides a neat visual reqresentation of the application’s UI.

A JavaScript file containing JSX will have to be compiled before it reaches a web browser.

```javascipt
import React from 'react';

const App = () => {
  return (
    <React.Fragment>
      <button onClick={() => 'The button was clicked!'}>Click!</button>
    </React.Fragment>
  );
};
```

## Components

In React, components are pieces of reusable, independent code that make up the user interface (UI) of the application. Each component comes with one or both of the following:

- A state object that contains component data that is expected to change over time.
- A props object with data that can be passed down from parent component to child component.

There are two types of components:
1. **Functional components**:Function components are stateless and only use the return statement. No import statement necessary.

```jsx
function FunctionComponent(props) {
  return (
    <div>
      ...
    <div>
  )
}
```

2. **Class-based components**:Class components contain a state and use a render() function to return JSX markup. When defined, the class has to be an extension of the React.Component.

```javascipt
import React from 'react';

class ClassComponent extends React.Component {
  this.state = {
    property1: "A string",
    property2: 1,
    property3: true
  }

  render() {
    return (
      <div>
        ...
      <div>
    )
  };
};

```



## Virtual DOM

React uses a Virtual DOM, a lightweight copy of the actual DOM stored in memory. When changes occur in the DOM, React compares the Virtual DOM to identify what changed and updates only those parts of the DOM. This approach is more efficient than updating the entire DOM.
To learn more refer [React Virtulal DOM](/posts/2021-react-basics)

## Props

Props (short for properties) allow information to be passed to a component. They are similar to global variables or objects and can be used in both class-based and functional components.

In React, components are able to use props, or “properties”, to display and share data throughout the application. In other words, props is the information that gets passed from one component to another.

```javascript
import React from 'react';

class ParentComponent extends React.Component {
  render() {
    return <ChildComponent prop1="Mike" prop2="piza">
  }
}

function ChildComponent(props) {
  return <h2>This is prop1: {props.prop1}. This is prop2: {props.prop2}.</h2>
}

```


Parent components can pass props to their child components, but not the other way around. Props can be many data types, including:

Numbers
Strings
Functions
Objects

## React is Declarative

React allows developers to describe UIs declaratively, specifying what they want, and React takes care of the how. It translates declarative descriptions into the actual UI in the browser.

## Optimizing Performance

React uses various techniques to optimize performance, including production builds, bundlers like Webpack, and profiling with developer tools. These techniques help achieve a fast user interface without extensive manual optimizations.

## Conditional Rendering

In React, you can render components conditionally. While you can't use if-else statements directly in JSX, you can use the ternary operator or helper functions to conditionally render components.

