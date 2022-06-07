# # 13. CLASSES

<br/>

## Q 13.1. Explain how prototypal inheritance works?

The Prototypal Inheritance is a feature in javascript used to add methods and properties in objects. It is a method by which an object can inherit the properties and methods of another object.

In order to get and set the [[Prototype]] of an object, we use `Object.getPrototypeOf()` and `Object.setPrototypeOf()`. Nowadays, in modern language, it is being set using `__proto__`.

**Syntax:**

```js
ChildObject.__proto__ = ParentObject
```

**Example:**

In the given example, there are two objects **ParentUser** and **ChildUser**. The object ChildUser inherits the methods and properties of the object ParentUser and further uses them.

```js
// Parent Object
let ParentUser = {
  talk: true,
  Canfly() {
    return "Sorry, Can't fly";
  },
};

// Child Object
let ChildUser = {
  CanCode: true,
  CanCook() {
    return "Can't say";
  },

  //  Inheriting the properties and methods of Parent Object
  __proto__: ParentUser,
};

// Property of Parent Object
console.log("Can a User talk?: " + ChildUser.talk);

// Method of ParentUser
console.log("Can a User fly?: " + ChildUser.Canfly());

// Property of ChildUser
console.log("Can a User code?: " + ChildUser.CanCode);

// Method of ChildUser
console.log("Can a User cook?: " + ChildUser.CanCook());
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-prototypal-inheritance-qxp33h?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 13.2. What is the difference between prototype and __proto__ in JavaScript?

**1. Proto**: 

It is an actual object that provides a way inherit to inherit properties from JavaScript with the help of an object which is created with new. Every object with behavior associated has internal property [[prototype]].

**Syntax:**

```js
Object.__proto__ = value
```

**Example:**

```js
function Employee(id, name) {
  this.id = id;
  this.name = name;
}
const employee = new Employee(1090, "Sarvesh Ghose");

// Object have proto property
employee

// Also if apply strict equal to check
// if both point at the same
// location then it will return true.
Employee.prototype === employee._proto_ // false
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-proto-sqkxeb?file=/src/index.js)**

**2. Prototype**: 

It is a special object which means it holds shared attributes and behaviors of instances. It is a way to inherit properties from javascript as it is available in every function declaration.

**Syntax:**

```js
objectTypeName.prototype.SharedPropertyName = value;
```

**Example:**

```js
// Constructor function
function Employee(id, name) {
  this.id = id;
  this.name = name;
}

// Objects
const employee = new Employee(3325, "Karishma Som");

// Prototype
Employee.prototype.getName = function () {
  return this.name;
};

// Function call using object
console.log(employee.getName());
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-prototype-wvh93l?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 13.3. What are the differences between ES6 class and ES5 function constructors?

Classes are a template for creating objects. They encapsulate data with code to work on that data. Classes in JS are built on prototypes but also have some syntax and semantics that are not shared with ES5 class-like semantics. 

ES6 Classes formalize the common JavaScript pattern of simulating class-like inheritance hierarchies using functions and prototypes. They are effectively simple sugaring over prototype-based OO, offering a convenient declarative form for class patterns which encourage interoperability.

ES6 Class Properties

* Class keyword
* getter/setter method
* constructor function
* extends keyword
* super keyword
* static keyword

**Example:** ES5 Function Constructor

```js
// ES5 Function Constructor
function Student(name, studentId) {
  // Call constructor of superclass to initialize superclass-derived members.
  Person.call(this, name);

  // Initialize subclass's own members.
  this.studentId = studentId;
}

Student.prototype = Object.create(Person.prototype);
Student.prototype.constructor = Student;
```

**Example:** ES6 Class

```js
// ES6 Class
class Student extends Person {
  constructor(name, studentId) {
    super(name);
    this.studentId = studentId;
  }
}
```

It\'s much more verbose to use inheritance in ES5 and the ES6 version is easier to understand and remember.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 13.4. What is class expression in es6 class?

A class expression is another way to define a class. Class expressions can be named or unnamed. The name given to a named class expression is local to the class\'s body. However, it can be accessed via the name property.

**Example:**

```js
// Unnamed Class
let Rectangle = class {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
console.log(Rectangle.name); // Rectangle

// Named Class
let Triangle = class TriangleClass {
  constructor(base, height) {
    this.base = base;
    this.height = height;
  }
};
console.log(Triangle.name); // TriangleClass
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-class-expression-nqbyr2?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 13.5. What is difference between private, public and static variables?

Private variables can be accessed by all the members (functions and variables) of the owner object but not by any other object. Public variables can be accessed by all the members of the owner as well as other objects that can access the owner.
Static variables are related to a class. They come into existence as soon as a class come into existence.

**Example:**

```js
// Constructor Function
function MyClass () {
 
  var privateVariable = "I am private!";  // Private variable 
  this.publicVariable = "I am public!";  // Public variable 

  this.publicMethod = function () {  // Public Method
    return privateVariable;
  };
}

// Instance method will be available to all instances but only load once in memory 
MyClass.prototype.publicMethod = function () {    
  return this.publicVariable;
};

// Static variable shared by all instances
MyClass.staticProperty = "I am static!";

var myInstance = new MyClass();

console.log(myClass.publicMethod()); // I am private! 
console.log(MyClass.staticProperty); // I am static! 
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-variable-scope-rgjsm4?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 13.6. What is difference between Classic Inheritance and Prototypical Inheritance?

**1. Class Inheritance**: 

Instances inherit from classes (like a blueprint — a description of the class), and create sub-class relationships: hierarchical class taxonomies. Instances are typically instantiated via constructor functions with the new keyword. Class inheritance may or may not use the class keyword from ES6.

**2. Prototypal Inheritance**: 

Instances inherit directly from other objects. Instances are typically instantiated via factory functions or Object.create(). Instances may be composed from many different objects, allowing for easy selective inheritance.

**Features**  

* Classes: create tight coupling or hierarchies/taxonomies.
* Prototypes: mentions of concatenative inheritance, prototype delegation, functional inheritance, object composition.
* No preference for prototypal inheritance & composition over class inheritance.

The difference between classical inheritance and prototypal inheritance is that classical inheritance is limited to classes inheriting from other classes while prototypal inheritance supports the cloning of any object using an object linking mechanism. A prototype basically acts as a template for other objects, whether they are extending the base object or not.

**Example:**

```js
function Circle(radius) {
  this.radius = radius;
}

Circle.prototype.area = function () {
  let radius = this.radius;
  return Math.PI * radius * radius;
};

Circle.prototype.circumference = function () {
  return 2 * Math.PI * this.radius;
};

const circle = new Circle(5);

console.log(circle.area()); // 78.53981633974483
console.log(circle.circumference()); // 31.41592653589793
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-prototypical-inheritance-iyxh6u?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 13.7. How do you create an object with prototype?

The `Object.create()` method is used to create a new object with the specified prototype object and properties. i.e, It uses existing object as the prototype of the newly created object. It returns a new object with the specified prototype object and properties.

**Example:**

```js
const user = {
  name: "Jayesh Sahni",
  printInfo: function () {
    console.log(`My name is ${this.name}.`);
  }
};

const admin = Object.create(user);
admin.name = "Disha Choudhry"; // Here, "name" is a property set on "admin" but not on "user" object
admin.printInfo(); // My name is Disha Choudhry
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-object-create-skyznx?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 13.8. How to use constructor functions for inheritance in JavaScript?

Let say we have `Person` class which has name, age, salary properties and **incrementSalary()** method.

```js
// Functions Constructor
function Person(name, age, salary) {
  this.name = name;
  this.age = age;
  this.salary = salary;
  this.incrementSalary = function (byValue) {
    this.salary = this.salary + byValue;
  };
}
```

Now we wish to create Employee class which contains all the properties of Person class and wanted to add some additional properties into Employee class.

```js
function Employee(company){
	this.company = company;
}

// Prototypal Inheritance 
Employee.prototype = new Person("Sundar Pichai", 24, 5000);
```

In the example above, **Employee** type inherits from **Person**. It does so by assigning a new instance of `Person` to `Employee` prototype. After that, every instance of `Employee` inherits its properties and methods from `Person`.

```js
// Prototypal Inheritance 
Employee.prototype = new Person("Sundar Pichai", 24, 5000);

var employee = new Employee("Google");

console.log(employee instanceof Person); // true
console.log(employee instanceof Employee); // true
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-prototypal-inheritance-djtiuh?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 13.9. What is prototype chain?

**Prototype chaining** is used to build new types of objects based on existing ones. It is similar to inheritance in a class based language. The prototype on object instance is available through `Object.getPrototypeOf(object)` or `__proto__` property whereas prototype on constructors function is available through **Object.prototype**.

**Example:**

```js
function Person(firstName, lastName, age) {
  this.firstName = firstName;
  this.lastName = lastName;
  this.age = age;
}
// Prototype chaining
Person.prototype.getFullName = function () {
  return this.firstName + " " + this.lastName;
};

// create an instance of the Person class
const person = new Person("Vanya", "Dayal", 25);

person.hasOwnProperty("firstName"); // true
person.hasOwnProperty("getFullName"); // false
person.getFullName(); // Vanya Dayal
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-prototype-chaining-9fvow6?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 13.10. What are javascript accessors?

ECMAScript 5 introduced javascript object accessors or computed properties through getters and setters. Getters uses `get` keyword whereas Setters uses `set` keyword.

```js
var user = {
  firstName: "John",
  lastName : "Abraham",
  language : "en",
  get lang() {
    return this.language;
  }
  set lang(lang) {
  this.language = lang;
  }
};

console.log(user.lang); // getter access lang as en
user.lang = 'fr';
console.log(user.lang); // setter used to set lang as fr
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 13.11. How do you define property on Object constructor?

The Object.defineProperty() static method is used to define a new property directly on an object, or modifies an existing property on an object, and returns the object. 

```js
const newObject = {};

Object.defineProperty(newObject, 'newProperty', {
  value: 100,
  writable: false
});

console.log(newObject.newProperty); // 100

newObject.newProperty = 200; // It throws an error in strict mode due to writable setting
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 13.12. What is the difference between get and defineProperty?

Both has similar results until unless you use classes. If you use `get` the property will be defined on the prototype of the object whereas using `Object.defineProperty()` the property will be defined on the instance it is applied to.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 13.13. What are the advantages of Getters and Setters?

Below are the list of benefits of Getters and Setters,

* They provide simpler syntax
* They are used for defining computed properties, or accessors in JS.
* Useful to provide equivalence relation between properties and methods
* They can provide better data quality
* Useful for doing things behind the scenes with the encapsulated logic.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 13.14. Can I add getters and setters using defineProperty method?

Yes, You can use `Object.defineProperty()` method to add Getters and Setters. For example, the below counter object uses increment, decrement, add and substract properties,

```js
var counterObj = {counter : 0};

// Define getters
Object.defineProperty(obj, "increment", {
  get : function () {this.counter++;}
});
Object.defineProperty(obj, "decrement", {
  get : function () {this.counter--;}
});

// Define setters
Object.defineProperty(obj, "add", {
  set : function (value) {this.counter += value;}
});
Object.defineProperty(obj, "subtract", {
  set : function (value) {this.counter -= value;}
});

obj.add = 10;
obj.subtract = 5;
console.log(obj.increment); //6
console.log(obj.decrement); //5
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 13.15. What is a decorator?

A decorator is an expression that evaluates to a function and that takes the target, name, and decorator descriptor as arguments. Also, it optionally returns a decorator descriptor to install on the target object. 

Let us define admin decorator for user class at design time,

```js
function admin(isAdmin) {
  return function(target) {
      target.isAdmin = isAdmin;
  }
}

@admin(true)
class User() {
}
console.log(User.isAdmin); // true

@admin(false)
class User() {
}
console.log(User.isAdmin); // false
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>
