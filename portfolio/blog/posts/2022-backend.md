---
title: "Building Backends with Node.js(express.js)"
subtitle: "Building Scalable Backends for Modern Web Applications"
date: "2022-10-12"
---
## Introduction
- Back-end developers deal with the hidden processes that run behind the scenes, building APIs and databases that power the front-end.

**4 Essential Parts** of Backend

1. HTTP Servers
2. Authentication
3. Databases
4. Middlewares

## JavaScript Refresher
Before we dive into backend development, let's start with a quick refresher on essential JavaScript concepts. We'll cover:

- Variables, Functions, and Scoping

- Promises and Async Javascript

- Inheritance and the DOM.

- Objects and Data Structures

This has been covered in detail here [Javascript Refresher](/posts/2022-javascript-refresher)

## Node.js Basics
- Node.js is a runtime environment that allows you to execute JavaScript code on the server side. It's built on the V8 JavaScript engine and provides a powerful, event-driven, non-blocking I/O model that makes it ideal for building highly scalable and efficient server applications.

Here are some core concepts and advantages of using Node.js in backend development:

1. **JavaScript Everywhere**
One of the most significant advantages of Node.js is that it allows developers to use JavaScript for both frontend and backend development. This unification of the programming language simplifies the development process and enables full-stack JavaScript development.

2. **Non-Blocking, Event-Driven Architecture**
Node.js operates on a non-blocking, event-driven architecture. This means that it can handle multiple concurrent requests without blocking the execution of other code. As a result, Node.js applications are highly performant and can scale efficiently to handle a large number of connections.

3. **Vast Ecosystem of Packages**
Node.js has a rich ecosystem of open-source packages available through npm (Node Package Manager). These packages cover a wide range of functionalities, from web frameworks like Express.js to database connectors, authentication libraries, and more. This extensive package ecosystem accelerates development and simplifies common tasks.

4. **Ideal for Real-Time Applications**
Node.js is well-suited for building real-time applications like chat applications, online gaming platforms, and collaborative tools. Its event-driven nature and support for WebSockets make it an excellent choice for handling real-time communication.

5. **Community and Support**
Node.js has a vibrant and active community of developers, which means you'll find ample resources, tutorials, and community support when working with Node.js.

6. **Cross-Platform Compatibility**
Node.js is cross-platform, making it compatible with Windows, macOS, and various Linux distributions. This ensures that your Node.js applications can run on a wide range of environments.



## HTTP Servers Components

1. Request Methods
2. URL Route
3. Query Parameter, Headers, Body
4. Status Codes
5. Response HTML, Text, JSON




**Protocols** : Communication between computers may sound simple, but there must be a set of rules to follow for effective communication between them. These rules are Protocols. 

Like on airport, there are set of rules that must be followed in order to get onboarded, which is Web Check-in, Luggage Check-In, Security Check. Similarly, for their computers to effectively communicate, we have certain set of rules and one of the popular protocol is **HTTP Protocol**.

- 💡 Like there is a protocol (set of rules) before we onboard in a plane, there is a popular HTTP Protocol for computers to communicate between each other over internet


**Another Reason Why do we need servers ? Apart from speed.**

Except these are powerful, For apps like Instagram, YouTube, LinkedIn, the content must be delivered at the moment, which should be new, personalized and updated. All this needs to stored somewhere, which are servers. Thus, we require a way to communicate with them.


## HTTP Server

---

**URL** : As we require a number to call a person, an address to send a courier, similarly we require URL (Uniform Resource Locator) to send a request to a specific server.



**Route/Path** : Now we know the address, but the server can do multiple things or in terms of programming it can execute multiple functions, so route tells which actions or code should be executed.


**Query Param, Header, Body** : All three are ways to send data to backend. Below is query parameter only.




**Request Method** : It is like mentioning what this request intended for, to create, read, update or delete data. In short CRUD.

![CRUD-operations](/images/CRUD.png)


💡 Default Request Method in browser is GET always. The moment you hit Enter, GET request sent.


- Although you can manage POST, PUT, DELETE via GET method using different routes, but that is not the ideal way or best practices.


## Creating Server using Express

---
Express.js, a web application framework for Node.js, enables you to build server applications in Node.js. As a backend application, it is the glue between your frontend application and a potential database or other data sources (e.g. REST APIs, GraphQL APIs).

Express.js is exchangeable with other web application frameworks for the backend the same way as React.js is exchangeable with Vue.js and Angular.js when it comes to frontend applications. The Node.js ecosystem doesn't offer only one solution, but various solutions that come with their strengths and weaknesses. However, for this application we will use a Express server, because it is the most popular choice when it comes to building JavaScript backend applications with Node.js.


-  Run `npm init -y`, this initializes the folder and creates `package.json` 


- 💡 `package.json` is like Project’s KYC (name, description, author etc) + dependencies (list of external libraries used) + scripts (commands for testing, debugging etc.)


-  Command to run, any JS file like `index.js` is `node index.js`


- 💡 `npm` (Node Package Manager) is a PlayStore of Node.js libraries.


-  **Importing Libraries**,
like we used `fs` library `const fs = require("fs");`  to read/write to a file, similarly we will use `Express` to create our own http server, the only catch is express library is not shipped with Node.js by default, so we have to install using command `npm install express`


-  💡 Think of `libraries` as chrome extensions or plugins that adds extra functionality and all we need to know is how to use, not how they are internally implemented.



- 💡 `node_modules` , this extra folder is like a luggage of guest who comes home to stay longer, that contains his essentials. Technically, this contains all libraries Express needs or express’s essential luggage.



- 💡 `package-lock.json`  stores the exact version of libraries being used in local environment. This is useful when I want to app on another machine with exact same versions.



## Adding Route

---
Routes in web applications for the backend are used to map URIs to middleware. These URIs could serve a text message, a HTML page, or data in JSON via REST or GraphQL. In a larger application, this would mean having several routes (middleware) which map to several URIs. In Express, a middleware is everything needed for a route, because routes are just another abstraction on top. Let's set up such a single route with Express:


- Adding Route, `/handleSum` that returns the sum of first 100 natural numbers. We can have as many routes we wish to have.

```jsx
const express = require('express')
const app = express()
const port = 3000

**function handleSum(req, res){
  var finalSum = 0;
  for(var i = 0; i < 100; i++){
    finalSum = finalSum + i;
  }
  var ans = `Sum is ${finalSum}`
  res.send(ans);
}

app.get('/handleSum', handleSum)**

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```



- ⚠️ `res.send()` method in Express expects a **string** or a **buffer**, not a number, either use `sum.toString()` ****or convert it to string prior in separate variable like above.


## Adding Query Parameter

---

Query Parameters are followed by a route and `?`, here we added a parameter name `counter` , to route handle sum `/handleSum?counter=10` that returns the sum up to that many numbers. We can have as many parameters we wish to have, separate them by `&`

```jsx
const express = require('express')
const app = express()
const port = 3000

function handleSum(req, res){
  var finalSum = 0;
	**var upTo = req.query.counter;**
  for(var i = 0; **i < upTo**; i++){
    finalSum = finalSum + i;
  }
  var ans = `Sum is ${finalSum}`
  res.send(ans);
}

app.get('/handleSum', handleSum)

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```

## Common questions

---

- **What if I do handle all POST, PUT, DELETE via GET ?**
Everything will be get stored in browser history, in case password is sent. It will be get stored.

- **I am getting 304 response, what does that mean ?**
When you receive a 304 response, it means that the requested resource has not been modified on the server since the browser's last access, and the browser can use its cached version of the resource instead of downloading it again.

- **Are there routes for every user on Instagram ?**
No, we use catch all route, looks like `app.get('/:username', searchUser)`



