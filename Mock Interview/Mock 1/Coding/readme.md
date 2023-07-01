<h2>How does the this keyword relate to lexical scope in javascript?</h2>
<br>
The this keyword in JavaScript refers to the current execution context. In lexical scope, the execution context is determined by the function that is currently being executed. <br>
This means that the this keyword will always refer to the object that created the function.
<br>
To understand the relationship between this and lexical scope, let's consider some examples
<br>
<br>
Example 1: Global Scope

```js
console.log(this);
```
In the global scope, outside of any function, this refers to the global object. However, when using strict mode ('use strict';), this will be undefined.

Example 2: Object Method
```js
const obj = {
  name: 'John',
  greet: function() {
    console.log(`Hello, ${this.name}!`);
  }
};

obj.greet();   // 'this' refers to the 'obj' object, so 'this.name' refers to 'obj.name'
```
Example 3: Constructor Function
```js
function Person(name) {
  this.name = name;
}
const john = new Person('John');
console.log(john.name);  // 'this' refers to the newly created object 'john'
```
When a function is used as a constructor with the new keyword, this refers to the newly created object. In this example, this.name sets the name property of the newly created Person object.

Example 4: Explicitly Setting this<br>
```js
function greet() {
  console.log(`Hello, ${this.name}!`);
}
const obj = {
  name: 'John'
};
greet.call(obj);  // using call() to explicitly set 'this' to 'obj'
```
By using the call() or apply() methods, you can explicitly set the value of this. In this example, greet.call(obj) sets this inside the greet function to obj, allowing this.name to access the name property of obj.
<br>
<br>

<h2>Can an object method access and modify the object's properties in javascript?</h2>
<br>
Yes, an object method in JavaScript can access and modify the object's properties. When a method is defined within an object, it has access to the object's properties through the this keyword. <br>The this keyword refers to the current instance of the object, allowing the method to access and modify the object's properties.

<br>

```js
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 30,
  greet: function() {
    console.log(`Hello, ${this.firstName} ${this.lastName}!`);
  },
  increaseAge: function() {
    this.age++;
  }
};

person.greet(); // Output: Hello, John Doe!
console.log(person.age); // Output: 30
person.increaseAge();
console.log(person.age); // Output: 31
```
<br>
<h2>How does middleware differ from an API gateway?</h2>
<br>
<li><b>Middleware</b> is a function or series of function that sits in between incoming request and outgoing response in application req-res cycle.</li>
<li><b>API gateway</b> is a specific type of middleware that designed to expose and manage APIs.</li>
<br>
In general, middleware is more general-purpose than API gateway. It can be used for a wider range of tasks, but it may not be as optimized for specific tasks such as API management. API gateway, on the other hand, is specifically designed for API management, so it typically offers more features and capabilities in this area.
<br>
<table>
<thead>
<tr>
<td><b>Feature</b></td>
<td>Middleware</td>
<td>API Gateway</td>
</tr>
</thead>
<tbody>
<tr>
<td><b>Purpose</b></td>
<td>Connects different systems and applications</td>
<td>Exposes API to external clients</td>
</tr>
<tr>
<td><b>Implementation</b></td>
<td>as a single piece of software or as collection of modules.</td>
<td>as a single piece of software.</td>
</tr>
<tr>
<td><b>Features</b></td>
<td>Data integration, security, performance optimization</td>
<td>Authentication, authorization, rate limiting, load balancing</td>
</tr>
<tr>
<td><b>Optimization</b></td>
<td>General-purpose</td>
<td>API management</td>
</tr>
</tbody>
</table>

<br>

<h2>Create a error handling middleware function</h2>
<br>

```js
const errorHandle=(err,req,res,next) => {
console.log(err);
if(err instanceof SyntaxError) {
res.status(404).send("Invalid request syntax")
}else if(err instanceof MongoDBError) {
res.status(500).send("mongodb error")
}else{
    res.status(500).send("Internal Server Error")
}
}

```

<br>

<h2>Write code that uses middleware to implement rate limiting in an API?</h2>
<br>

```js
const express = require('express');
const RateLimit = require('express-rate-limit');

const app = express();

// Create a rate limiter middleware
const limiter = new RateLimit({
  windowMs: 60 * 1000, // 1 minute window
  max: 100, // Maximum 100 requests per window
  message: 'Too many requests, please try again later.',
});

// Apply the rate limiter middleware to all routes
app.use(limiter);
```

<br>

<h2>Implement embedded relationship in node.js and mongodb using a blog post and comments so that you can create a new posts document with comments write the schema?</h2>
<br>

```js
const mongoose = require('mongoose');

const postSchema = new mongoose.Schema({
  title: {
    type: String,
    required: true
  },
  content: {
    type: String,
    required: true
  },
  comments: [{
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Comment'
  }]
});

const Post = mongoose.model('Post', postSchema);

module.exports = Post;


const mongoose = require('mongoose');

const commentSchema = new mongoose.Schema({
  text: {
    type: String,
    required: true
  },
  post: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Post'
  }
});
```

<br>

<h2>What is a RESTful API?</h2>

<h2>What is the React lifecycle?</h2>

<h2>how can you use the useEffect hook to clean up resources or subscription when a component unmounts?</h2>