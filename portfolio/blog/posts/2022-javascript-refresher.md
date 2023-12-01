---
title: "Javascript Refresher"
subtitle: "A Deep Dive into async/await, promises and arrow Functions"
date: "2022-9-11"
---

## JS Runtime/Event Loop

---

**Event Loop** is a way of running asynchronous code (background task) in JavaScript. 

- An async code is offloaded to “**Web APIs**”, (which is on *separate thread*) or so it keeps running in background and doesn't block the *main thread*. When this background task is completed, its callback is added to a “**Callback Queue**” and is pushed to “**Call Stack**”(when it is empty) by “**Event Loop**” and hence that callback executes on main thread.

## Callback & Promises

---

**Callback** : When we want to call a function after a task finishes. Like I want my friend to get Medicine2 once I receive the Medicine1 from him. Below is the code for the same.

```jsx
function getMedicine1(){
	console.log("1 Received");
	setTimeout(getMedicine2, 2000);
}

function getMedicine2(){
	console.log("2 Received");
}

setTimeout(getMedicine1, 1000);
```

**Callback Hell** : When the code above is written like below, this usually happens in complex code, which too much nested. This super ugly code is referred to as “Callback Hell”.

```jsx
setTimeout(function getMedicine1(){
 console.log("1 Received");
  setTimeout(function getMedicine2(){
	console.log("2 Received"); 
  }, 2000);
}, 1000);
```

**Promises** : In the solution to callback hell, promises were introduced.

```Javascript
function getMedicine1() {
  return new Promise(function(resolve, reject) {
    setTimeout(function() {
      console.log("1 Received")
      resolve();
    }, 1000);
  });
}

function getMedicine2() {
  return new Promise(function(resolve, reject) {
    setTimeout(function() {
			console.log("2 Received")
      resolve();
    }, 2000);
  });
}

getMedicine1().then(getMedicine2())
```

**Another Promise example :** Simulating an Asynchronous Operation (e.g., making an API request)

```jsx
const fetchData = new Promise((resolve, reject) => {
  setTimeout(() => {
    const data = { name: "John Doe", age: 25 };
    resolve(data); }
  , 2000);
});

fetchData
  .then((result) => {
    console.log("Data fetched:", result);
  })
  .catch((error) => {
    console.error("Error:", error);
  });
  ```


  
👇🏻 Summarization of **Callback** and **Promise**



**Callbacks**: Function provided to be called back when task completes.

**Promises**: Immediate promise received, allowing chaining of functions based on fulfilment or rejection.
```jsx
function printContent(error, data) {
	console.log(data);
}

fs.read("file.txt", printContent) // Callback Version
fs.read("file.txt").then(printContent) // Promise Version
```


## What is async and await?
Handling asynchronous actions in JavaScript was originally done using callback functions. But the ES6 version of JavaScript introduced Promises and the .then() and .catch() syntax.

After ES6, the JavaScript language has continued to evolve and provide even more ways of handling asynchronous actions, like async and await. 

- This new syntax allows developers to treat asynchronous code as if it were synchronous and write cleaner code without getting caught up in chaining .then()s and .catch()s. Take a look below, the first example is using the .then() method:

```jsx
myPromise()
  .then((resolvedValue) => {
    console.log(resolvedValue);
  });
```

Now compare it with using async and await:

```Jsx
const myAsyncFunc = async () => {
  let resolvedValue = await myPromise();
  console.log(resolvedValue);
};
```

- Both code snippets do the same thing! The async keyword makes the function capable of handling asynchronous code, that has the await keyword. Both keywords are syntactic sugar — it doesn’t introduce new functionality into the language, it makes it slightly easier to write and read

## Arrow functions
- Up-to-date browsers now support most of the ES6 features which allow developers to take advantage of these new additions. ES6 ultimately allows programmers to save time and write more concise code. Take for example pre-ES6 syntax for function expressions:

```Jsx
var greeting = function() {
  console.log('Hello World!');  
};

With ES6 arrow functions, we can transform the expression above into:

const greeting = () => console.log('Hello World'); 
```