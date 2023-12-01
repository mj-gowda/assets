---
title: "React: The Magic of React's Virtual DOM"
subtitle: "Unraveling the Secrets of React's Performance Optimization"
date: "2021-06-04"
---

## What is the React DOM and React Virtual DOM

React DOM is a virtual representation of the real Document Object Model (DOM) in web browsers.
It's a lightweight copy used by React to optimize rendering performance.

- Re-rendering the entire DOM can be inefficient when data changes in a web app.
React's **Virtual DOM** minimizes this by computing minimal updates to the real DOM.

**In React, virtual DOM is a conceptual representation of the actual DOM object, like a lightweight copy. A virtual DOM object has the same properties as a real DOM object, but it lacks the real thing’s power to directly change what’s on the screen.**

Manipulating the DOM is slow. Manipulating the virtual DOM is much faster, because nothing gets drawn onscreen. Think of manipulating the virtual DOM as editing a blueprint, as opposed to moving rooms in an actual house.

## How React Uses the Virtual DOM

### React's Virtual DOM Workflow
![virtual dom](/images/react1.png/)

1. **Initial Render**: When rendering a user interface in React, it creates a virtual DOM tree representing the UI and stores it in memory.

2. **Subsequent Updates**: When data changes, React automatically creates a new virtual DOM tree for the update.

3. **Virtual DOM Comparison**:
   - React compares the new virtual DOM tree to the previous one.
   - It uses a diffing algorithm called **Reconciliation** to identify changes.

4. **Minimized Updates**: After reconciliation, React uses a renderer library like ReactDOM to update the real DOM.
   - Only the nodes with changes get updated and repainted in the actual DOM.
   - This process minimizes performance overhead.

5. **Efficient Rendering**: React ensures that the updated node matches the actual DOM, preserving input values and preventing unnecessary re-renders.

6. **Diffing Process**:
   - React starts by comparing root elements in both snapshots.
   - If the elements match, it checks attributes and then proceeds to children.
   - If elements differ, React rebuilds the affected part of the DOM.

7. **Example**: Changing from a `span` to a `div` would result in rebuilding the DOM nodes.

React's virtual DOM efficiently updates only what's necessary, optimizing UI performance and ensuring consistent user experiences.

