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
<br>
<h2>How does middleware differ from an API gateway?</h2>
<br>
