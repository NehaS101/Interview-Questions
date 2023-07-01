<h2>How does the this keyword relate to lexical scope in javascript?</h2>
The this keyword in JavaScript refers to the current execution context. In lexical scope, the execution context is determined by the function that is currently being executed. <br>
This means that the this keyword will always refer to the object that created the function.
<br>
To understand the relationship between this and lexical scope, let's consider some examples
<br>
<br>
Example 1: Global Scope
console.log(this);

In the global scope, outside of any function, this refers to the global object. However, when using strict mode ('use strict';), this will be undefined.

Example 2: Object Method

const obj = {<br>
  name: 'John',<br>
  greet: function() {<br>
    console.log(`Hello, ${this.name}!`);<br>
  }
};

obj.greet();   // 'this' refers to the 'obj' object, so 'this.name' refers to 'obj.name'

Example 3: Constructor Function<br>
function Person(name) {<br>
  this.name = name;<br>
}<br>
const john = new Person('John');<br>
console.log(john.name);  // 'this' refers to the newly created object 'john'

When a function is used as a constructor with the new keyword, this refers to the newly created object. In this example, this.name sets the name property of the newly created Person object.

Example 4: Explicitly Setting this<br>
function greet() {<br>
  console.log(`Hello, ${this.name}!`);<br>
}<br>
const obj = {<br>
  name: 'John'<br>
};<br>
greet.call(obj);  // using call() to explicitly set 'this' to 'obj'

By using the call() or apply() methods, you can explicitly set the value of this. In this example, greet.call(obj) sets this inside the greet function to obj, allowing this.name to access the name property of obj.

<h2>Can an object method access and modify the object's properties in javascript?</h2>

Yes, an object method in JavaScript can access and modify the object's properties. When a method is defined within an object, it has access to the object's properties through the this keyword. <br>The this keyword refers to the current instance of the object, allowing the method to access and modify the object's properties.
<br>
const person = {<br>
  firstName: 'John',<br>
  lastName: 'Doe',<br>
  age: 30,<br>
  greet: function() {<br>
    console.log(`Hello, ${this.firstName} ${this.lastName}!`);<br>
  },<br>
  increaseAge: function() {<br>
    this.age++;<br>
  }<br>
};<br>

person.greet(); // Output: Hello, John Doe!<br>
console.log(person.age); // Output: 30
<br>
person.increaseAge();<br>
console.log(person.age); // Output: 31<br>
