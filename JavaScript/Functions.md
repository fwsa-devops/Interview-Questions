## # 9. FUNCTIONS

<br/>

## Q 9.1. What are the benefits of using arrow function over es5 function?

Arrows is a new syntax for functions, which brings several benefits:

* Arrow syntax automatically binds `this` to the surrounding code\'s context
* The syntax allows an implicit return when there is no body block, resulting in shorter and simpler code in some cases
* Last but not least, `=>` is shorter and simpler than `function`, although stylistic issues are often subjective

**Example 01:** Arrow Function with No Argument

If a function doesn\'t take any argument, then you should use empty parentheses.

```js
let greet = () => console.log('Hello');
greet(); // Hello
```

**Example 02:** Arrow Function with One Argument

If a function has only one argument, you can omit the parentheses.

```js
let greet = x => console.log(x);
greet('Hello'); // Hello 
```

**Example 03:** Arrow Function as an Expression

You can also dynamically create a function and use it as an expression.

```js
let age = 25;

let welcome = (age < 18) ?
  () => console.log('Baby') :
  () => console.log('Adult');

welcome(); // Adult
```

**Example 04:** Multiline Arrow Functions

If a function body has multiple statements, you need to put them inside curly brackets `{}`.

```js
let area = (r) => {
  const pi = 3.14;
  return pi * r * r;
}

let result = area(10);
console.log(result); // 314
```

*Note: Unlike regular functions, arrow functions do not have their own `this`. The value of `this` inside an arrow function remains the same throughout the lifecycle of the function and is always bound to the value of `this` in the closest non-arrow parent function.*

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-arrow-function-yl7oqo?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.2. What is the benefit of using the arrow syntax for a method in a constructor?

The main advantage of using an arrow function as a method inside a constructor is that the value of `this` gets set at the time of the function creation and can\'t change after that. So, when the constructor is used to create a new object, `this` will always refer to that object.

```js
const Person = function(firstName) {
  this.firstName = firstName;
  this.sayName1 = function() { console.log(this.firstName); };
  this.sayName2 = () => { console.log(this.firstName); };
};

const john = new Person('John');
const dave = new Person('Dave');

john.sayName1(); // John
john.sayName2(); // John

// The regular function can have its 'this' value changed, but the arrow function cannot
john.sayName1.call(dave); // Dave (because "this" is now the dave object)
john.sayName2.call(dave); // John

john.sayName1.apply(dave); // Dave (because 'this' is now the dave object)
john.sayName2.apply(dave); // John

john.sayName1.bind(dave)(); // Dave (because 'this' is now the dave object)
john.sayName2.bind(dave)(); // John

var sayNameFromWindow1 = john.sayName1;
sayNameFromWindow1(); // undefined (because 'this' is now the window object)

var sayNameFromWindow2 = john.sayName2;
sayNameFromWindow2(); // John
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.3. Difference between `Function`, `Method` and `Constructor` calls in JavaScript?

If your are familiar with Object-oriented programming, More likely familiar to thinking of functions, methods, and class constructors as three separate things. But In JavaScript, these are just three different usage patterns of one single construct.

functions : The simplest usages of function call:

```js
function helloWorld(name) {
  return "hello world, " + name;
}

helloWorld("JS Geeks"); // "hello world JS Geeks"
```

Methods in JavaScript are nothing more than object properties that are functions.

```js
var obj = {
  helloWorld : function() {
    return "hello world, " + this.name;
  },
  name: 'John Carter'
}
obj.helloWorld(); // // "hello world John Carter"
```

Notice how `helloWorld` refer to `this` properties of obj. Here It is clear or you might have already understood that `this` gets bound to `obj`. But the interesting point that we can copy a reference to the same function `helloWorld` in another object and get a difference answer. Let see:

```js
var obj2 = {
  helloWorld : obj.helloWorld,
  name: 'John Doe'
}
obj2.helloWorld(); // "hello world John Doe"
```

You might be wonder what exactly happens in a method call here. Here we call the expression itself determine the binding of this `this`, The expression `obj2.helloWorld()` looks up the `helloWorld` property of obj and calls it with receiver object `obj2`.

The third use of functions is as constructors. Like function and method, `constructors` are defined with function.

```js
function Employee(name, age) {
  this.name = name;
  this.age = age;
}

var emp1 = new Employee('John Doe', 28);
emp1.name; // "John Doe"
emp1.age; // 28
```

Unlike function calls and method calls, a constructor call `new Employee('John Doe', 28)` creates a brand new object and passes it as the value of `this`, and implicitly returns the new object as its result.

The primary role of the constructor function is to initialize the object.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.4. When you should not use arrow functions in ES6?

An arrow function is a shorter syntax for a function expression and does not have its own **this, arguments, super, or new.target**. These function are best suited for non-method functions, and they cannot be used as constructors.

**Arrow functions in ES6 has two limitations:**

* Do not work with new
* Fixed this bound to scope at initialisation

**When should not use Arrow Functions:**

**1. Object methods:**  

The counter object has two methods: current() and next(). The current() method returns the current counter value and the next() method returns the next counter value.

```js
// Usin arrow function
const counter = {
  count: 0,
  next: () => ++this.count,
  current: () => this.count
};

console.log(counter.next()); // NaN
```

**2. Event handlers:**  

If we click the button, we would get a TypeError. It is because this is not bound to the button, but instead bound to its parent scope.

```js
let button = document.getElementById('press');

button.addEventListener('click', () => {
  this.classList.toggle('on');
});
```

**3. Prototype methods:**

The `this` value in these `next()` and `current()` methods reference the global object. Since the `this` value inside the methods to reference the Counter object, it needs to use the regular functions instead

```js
function Counter() {
    this.count = 0;
}

Counter.prototype.next = () => {
    return this.count;
};

Counter.prototype.current = () => {
    return ++this.next;
}
```

**4. Functions that use the arguments object:**

Arrow functions don\'t have the arguments object. Therefore, if a function that uses arguments object, you cannot use the arrow function.

```js
const concat = (separator) => {
    let args = Array.prototype.slice.call(arguments, 1);
    return args.join(separator);
}
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-arrow-function-52ny7c?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.5. What are the properties of function objects in javascript?

**JavaScript function objects** are used to define a piece of JavaScript code. This code can be called within a JavaScript code as and when required.

**Javascript Function Objects Property:**

|Name             |Description                       |
|-----------------|----------------------------------|
|arguments        |An array corresponding to the arguments passed to a function.|
|arguments.callee |Refers the currently executing function.|
|arguments.length |Refers the number of arguments defined for a function.|
|constructor      |Specifies the function that creates an object.|
|length           |The number of arguments defined by the function.|
|prototype        |Allows adding properties to a Function object.|

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.6. What is a first class function?

In javaScript, functions can be stored as a variable inside an object or an array as well as it can be passed as an argument or be returned by another function. That makes function **first-class function** in JavaScript.

**Example 01:** Assign a function to a variable

```js
const message = function() {
   console.log("Hello World!");
}

message(); // Invoke it using the variable
```

**Example 02:** Pass a function as an Argument

```js
function sayHello() {
   return "Hello, ";
}
function greeting(helloMessage, name) {
  console.log(helloMessage() + name);
}
// Pass `sayHello` as an argument to `greeting` function
greeting(sayHello, "JavaScript!");
```

**Example 03:** Return a function

```js
function sayHello() {
   return function() {
      console.log("Hello!");
   }
}
```

**Example 04:** Using a variable

```js
const sayHello = function() {
   return function() {
      console.log("Hello!");
   }
}
const myFunc = sayHello();
myFunc();
```

**Example 05:** Using double parentheses

```js
function sayHello() {
   return function() {
      console.log("Hello!");
   }
}
sayHello()();
```

We are using double parentheses `()()` to invoke the returned function as well.

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-first-class-function-ckck8k?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.7. What is a higher order function?

A Higher-Order function is a function that receives a function as an argument or returns the function as output.

For example, `Array.prototype.map()`, `Array.prototype.filter()` , `Array.prototype.forEach()` and `Array.prototype.reduce()` are some of the Higher-Order functions in javascript.

**Example 01:** .map()

```js
const array = [10, 20, 30];

const result = array.map(function (item) {
  return item * 2;
});
console.log(result); // [20, 40, 60]
```

**Example 02:** .filter()

```js
const randomNumbers = [4, 11, 42, 14, 39];

const filteredArray = randomNumbers.filter((number) => {
  return number > 15;
});
console.log(filteredArray); // [42, 39]
```

**Example 03:** .forEach()

```js
const numbers = [28, 77, 45];

numbers.forEach((number) => {
  console.log(number);
});
```

**Example 04:** .reduce()

```js
const arrayOfNumbers = [10, 20, 30];

const sum = arrayOfNumbers.reduce((accumulator, currentValue) => {
  return accumulator + currentValue;
});
console.log("Sum: " + sum); // 60
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-higher-order-function-yhbo9v?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.8. What is a unary function?

Unary function (i.e. monadic) is a function that accepts exactly one argument. It stands for single argument accepted by a function.

```js
// Unary function
const unaryFunction = (number) => number + 10;

console.log(unaryFunction(10)); // 20
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-unary-function-j0h3gh?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.9. What is currying function?

Currying is the process of taking a function with multiple arguments and turning it into a sequence of functions each with only a single argument.

In other words, when a function, instead of taking all arguments at one time, takes the first one and return a new function that takes the second one and returns a new function which takes the third one, and so forth, until all arguments have been fulfilled.

```js
// Normal function
const add = (a, b, c) => {
  return a + b + c;
};
console.log(add(10, 10, 10)); // 30

// Currying function
const addCurry = (a) => {
  return (b) => {
    return (c) => {
      return a + b + c;
    };
  };
};
console.log(addCurry(20)(20)(20)); // 60
```

*Note: Curried functions are great to improve code re-usability and functional composition.*

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-currying-function-3kq1db?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.10. What is a pure function?

Pure functions are functions that accept an input and returns a value without modifying any data outside its scope(Side Effects). Its output or return value must depend on the input/arguments and pure functions must return a value.

**Example:** Pure Function

It is a pure function because you always get a Hello `<name>` as output for the `<name>` pass as an input.

```js
// Pure Function

function sayGreeting(name) {
  return `Hello ${name}`;
}

console.log(sayGreeting("World"));
```

**Example:** Not Pure Function

The function\'s output now depends on an outer state called greeting. What if someone changes the value of the greeting variable to `Hola`? It will change the output of the `sayGreeting()` function even when you pass the same input.

```js
let greeting = "Hello";

function sayGreeting(name) {
  return `${greeting} ${name}`;
}
```

A function must pass two tests to be considered **pure**:

* Same inputs always return same outputs
* No side-effects

**Benefits:**

* **Predictable**: It produces a predictable output for the same inputs.
* **Readable**: Anyone reading the function as a standalone unit can understand its purpose completely.
* **Reusable**: Can reuse the function at multiple places of the source code without altering its and the caller's behavior.
* **Testable**: We can test it as an independent unit.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.11. What is memoization in JavaScript?

Memoization is a programming technique which attempts to increase a function\'s performance by **caching** its previously computed results.  

Each time a memoized function is called, its parameters are used to index the cache. If the data is present, then it can be returned, without executing the entire function. Otherwise the function is executed and then the result is added to the cache.

```js
// Memoized function to Add Number

const memoizedAdd = () => {
  let cache = {};
  return (number) => {
    if (number in cache) {
      console.log('Fetching from cache: ');
      return cache[number];
    }
    else {
      console.log('Calculating result: ');
      let result = number + 10;
      cache[number] = result;
      return result;
    }
  }
}
// returned function from memoizedAdd
const sum = memoizedAdd();

console.log(sum(10)); // Calculating result: 20
console.log(sum(10)); // Fetching from cache: 20
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-memoized-function-kykkp7?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.12. What is an arguments object?

The arguments object is an Array-like object ( `arguments` ) accessible inside functions that contains the values of the arguments passed to that function.

**Example:**

```js
// arguments object

function sum() {
  let total = 0;
  for (let i = 0, len = arguments.length; i < len; ++i) {
    total += arguments[i];
  }
  return total;
}

sum(10, 20, 30); // returns 60
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-arguments-object-od6s7l?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.13. What is the way to find the number of parameters expected by a function?

The **length** property indicates the number of parameters expected by the function.

```js
// function.length

function fun1() {}
console.log(fun1.length); // 0

function fun2(arg1, arg2) {}
console.log(fun2.length); // 2
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-function-length-7btkvr?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.14. What is the difference between Call, Apply and Bind?

* **Call** invokes the function and allows you to pass in arguments one by one.
* **Apply** invokes the function and allows you to pass in arguments as an array.
* **Bind** returns a new function, allowing you to pass in a this array and any number of arguments.

**Example:** `call()`

```js
const employee1 = { firstName: "Sahima", lastName: "Mutti" };
const employee2 = { firstName: "Aarush", lastName: "Krishna" };

function say(greeting) {
  console.log(greeting + " " + this.firstName + " " + this.lastName);
}

say.call(employee1, "Hi");    // Hi Sahima Mutti 
say.call(employee2, "Hello"); // Hello Aarush Krishna 
```

**Example:** `apply()`

```js
const employee1 = { firstName: "Sahima", lastName: "Mutti" };
const employee2 = { firstName: "Aarush", lastName: "Krishna" };

function say(greeting) {
  console.log(greeting + " " + this.firstName + " " + this.lastName);
}

say.apply(employee1, ["Hi"]);    // Hi Sahima Mutti 
say.apply(employee2, ["Hello"]); // Hello Aarush Krishna 
```

**Example:** `bind()`

```js
const employee1 = { firstName: "Sahima", lastName: "Mutti" };
const employee2 = { firstName: "Aarush", lastName: "Krishna" };

function say(greeting) {
  console.log(greeting + " " + this.firstName + " " + this.lastName);
}

var sayEmployee1 = say.bind(employee1);
var sayEmployee2 = say.bind(employee2);

sayEmployee1("Hi");    // Hi Sahima Mutti 
sayEmployee2("Hello"); // Hello Aarush Krishna 
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-call-apply-bind-xwenyv?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.15. What is bind method in javascript?

The `bind()` method creates a new function, when invoked, has the `this` sets to a provided value. The `bind()` method allows an object to borrow a method from another object without making a copy of that method. This is known as function **borrowing** in JavaScript.

**Example:**

```js
// bind() function

const person = {
  firstName: "Chhavi",
  lastName: "Goswami",
  fullName: function () {
    return this.firstName + " " + this.lastName;
  }
};

const member = {
  firstName: "Vasuda",
  lastName: "Sahota"
};

let fullName = person.fullName.bind(member);
console.log(fullName()); // Vasuda Sahota
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-bind-gdspfz?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.16. What is an anonymous function?

An anonymous function is a function without a name. Anonymous functions are commonly assigned to a variable name or used as a callback function.

**Example 01:** Anonymous function

```js
let show = function () {
  console.log("Anonymous function");
};
show();
```

**Example 02:** anonymous functions as arguments

```js
setTimeout(function () {
  console.log("Execute later after 1 second");
}, 1000);
```

**Example 03:** Immediately invoked function execution

```js
const person = {
  firstName: "Ayaan",
  lastName: "Memon"
};

(function () {
  console.log(person.firstName + " " + person.lastName); // Ayaan Memon
})(person);
```

**Example 04:** Arrow functions

```js
let add = (a, b) => a + b;

add(10, 20); // 30
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-anonymous-function-vilo1d?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.17. Explain the difference between `function foo() {}` and `var foo = function() {}`?

**1. Function Declaration:**

Function declarations are evaluated upon entry into the enclosing scope, before any step-by-step code is executed. The function\'s name (`foo`) is added to the enclosing scope.

```js
foo(); // Function Declaration Example!

function foo() {
  console.log("Function Declaration Example!");
}
```

**2. Function Expression:**

Function expressions are evaluated as part of the step-by-step code, at the point where they appear. That one creates a function with no name, which it assigns to the foo variable.

```js
foo(); // TypeError: foo is not a function

var foo = function() {
  console.log(typeof foo); // function
};
console.log(typeof foo);     // undefined
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-function-erlj09?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.18. When to use function declarations and expressions in JavaScript?

**Function Declarations:**

A declared function is "saved for later use", and will be executed later, when it is invoked (called).

```js
// Function declaration
function add(num1, num2) {
	return num1 + num2;
}
```

function is only declared here. For using it, it must be invoked using function name. e.g add(10, 20);  

**Function Expression:**

A function expression can be stored in a variable:

```js
// Function expression
var add = function (num1, num2) {
	return num1 + num2;
};
```

After a function expression has been stored in a variable, the variable can be used as a function. Functions stored in variables do not need function names. They are always invoked (called) using the variable name.

**Difference:**

* `Function declarations` load before any code is executed while `Function expressions` load only when the interpreter reaches that line of code.
* Similar to the `var` statement, function declarations are hoisted to the top of other code. Function expressions aren\'t hoisted, which allows them to retain a copy of the local variables from the scope where they were defined.  

**Benefits of Function Expressions:**  

There are several different ways that function expressions become more useful than function declarations.

* As closures
* As arguments to other functions
* As Immediately Invoked Function Expressions (IIFE)

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.19. What is the difference between a method and a function in javascript?

**1. Function:**

A function is a piece of code that is called by name and function itself not associated with any object and not defined inside any object. It can be passed data to operate on (i.e. parameter) and can optionally return value.

**Example:**

```js
// Function 
function message(msg) {
  return msg;
}

// Call the function
message("Welcome to JavaScript");
```

Here, `message()` function call is not associated with `object` hence not invoked through any object.

**2. Method:**

A JavaScript method is a property of an object that contains a function definition. Methods are functions stored as object properties.

**Example:**

```js
// Method
let employee = {
  firstName: "Ajay",
  lastName: "Nagi",
  getName: function () {
    return "Employe Name: " + this.firstName + " " + this.lastName;
  }
};

// Call the method
console.log(employee.getName());
```

Here `employee` is an object and `getName` is a method which is associated with `employee`.

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-function-vs-method-rw9dmj?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.20. What is Function binding?

Function binding ( `.bind()` ) is a method on the prototype of all functions in JavaScript. It allows to create a new function from an existing function, change the new function\'s `this` context, and provide any arguments you want the new function to be called with. The arguments provided to `bind` will precede any arguments that are passed to the new function when it is called.

**Example:**

```js
// Function Binding
const person = {
  firstName: "Nirupama",
  lastName: "Randhawa",
  getName: function () {
    return this.firstName + " " + this.lastName;
  }
};

const member = {
  firstName: "Alisha",
  lastName: "Chhabra"
};

let getName = person.getName.bind(member);
console.log(getName()); // Alisha Chhabra
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-function-binding-od3zjg?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.21. Explain how `this` works in JavaScript?

The `this` keyword refers to an `object`. Which object depends on how this is being invoked (used or called). The `this` keyword refers to different objects depending on how it is used.

* In an object method, `this` refers to the object.
* Alone, `this` refers to the global object.
* In a function, `this` refers to the global object.
* In a function, in strict mode, `this` is `undefined`.
* In an event, `this` refers to the element that received the event.
* Methods like `call()`, `apply()`, and `bind()` can refer `this` to any object.

**Example:**

```js
// this keyword in object method

const person = {
  firstName: "Nirupama",
  lastName: "Randhawa",
  getName: function () {
    return this.firstName + " " + this.lastName;
  }
};
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.22. What is generator in JS?

**Generator-Function:**

A generator-function is defined like a normal function, but whenever it needs to generate a value, it does so with the `yield` keyword rather than `return`. The `yield` statement suspends function\'s execution and sends a value back to caller, but retains enough state to enable function to resume where it is left off. When resumed, the function continues execution immediately after the last `yield` run.

**Syntax:**

```js
function* gen() {
     yeild 1;
     yeild 2;
     ...
     ...
}
```

**Generator-Object:**

Generator functions return a generator object. Generator objects are used either by calling the next method on the generator object or using the generator object in a "for in" loop.

**Example:**

```js
// Generate Function

function* fun() {
  yield 10;
  yield 20;
  yield 30;
}

// Calling the Generate Function
var gen = fun();
gen.next().value; // 10
gen.next().value; // 20
gen.next().value; // 30
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-generate-function-si7ieh?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.23. Compare Async-Await and Generators usage to achive same functionality?

**1. Generators/Yield:**

Generators are objects created by generator functions — functions with an * (asterisk) next to their name. The yield keyword pauses generator function execution and the value of the expression following the yield keyword is returned to the generator's caller. It can be thought of as a generator-based version of the return keyword.

```js
// Generator function

const generator = (function* () {
  // waiting for .next()
  const number = yield 5;
  // waiting for .next()
  console.log(number); // => 15
})();

console.log(generator.next()); // => { done: false, value: 5 }
console.log(generator.next(15)); // => { done: true, value: undefined }
```

**2. Async/Await:**

Async keyword is used to define an asynchronous function, which returns a `AsyncFunction` object.

Await keyword is used to pause async function execution until a `Promise` is fulfilled, that is resolved or rejected, and to resume execution of the `async` function after fulfillments. When resumed, the value of the `await` expression is that of the fulfilled `Promise`.

**Key points:**  

1. Await can only be used inside an async function.
2. Functions with the async keyword will always return a promise.
3. Multiple awaits will always run in sequential order under a same function.
4. If a promise resolves normally, then await promisereturns the result. But in case of a rejection it throws the error, just if there were a throw statement at that line.
5. Async function cannot wait for multiple promises at the same time.
6. Performance issues can occur if using await after await as many times one statement doesn\'t depend on the previous one.

```js
// Async/Await

async function asyncFunction() {
  const promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve("resolved!"), 1000);
  });

  const result = await promise;
  // wait till the promise resolves (*)

  console.log(result); // "resolved!"
}

asyncFunction();
```

**Generator and Async-await — Comparison:**  

1. Generator functions/yield and Async functions/await can both be used to write asynchronous code that "waits", which means code that looks as if it was synchronous, even though it really is asynchronous.
2. Generator function are executed yield by yield i.e one yield-expression at a time by its iterator (the next method) where as Async-await, they are executed sequential await by await.
3. Async/await makes it easier to implement a particular use case of Generators.
4. The return value of Generator is always {value: X, done: Boolean} where as for Async function it will always be a promise that will either resolve to the value X or throw an error.
5. Async function can be decomposed into Generator and promise implementation which are good to know stuff.

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-generator-async-lhs021?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.24. How do you compare two date objects?

Two dates can be compared by converting them into numeric values using `date.getTime()` method to correspond to their time. Also,
the relational operators `<`, `<=`, `>`, `>=` can be used to compare JavaScript dates.

However, the equality operators `==`, `!=`, `===`, `!==` cannot be used to compare (the value of) dates because:

* Two distinct objects are never equal for either strict or abstract comparisons.
* An expression comparing Objects is only true if the operands reference the same Object.

**Example:**

```js
// Using getTime()
let d1 = new Date();
let d2 = new Date(d1);

console.log(d1.getTime() === d2.getTime()); // true

// Using '<' and '>'
let d3 = new Date(2022, 10, 31);
let d4 = new Date(2022, 10, 30);

console.log(d3 < d4); // true
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-date-comparison-lu76nj?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.25. What are closures?

A closure is the combination of a function and the lexical environment within which that function was declared. i.e, it is an inner function that has access to the outer or enclosing function\'s variables.

Closure is useful in hiding implementation detail in JavaScript. In other words, it can be useful to create private variables or functions. The closure has three scope chains

* Own scope where variables defined between its curly brackets
* Outer function\'s variables
* Global variables

**Example:**

```js
// Closures

function init() {
  let name = "JavaScript closures"; // name is a local variable created by init
  function displayName() {
    // displayName() is the inner function, a closure
    console.log(name); // use variable declared in the parent function
  }
  displayName();
}
init();
```

As per the above code, the inner `function displayName()` has access to the variables in the outer `function init()`.

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-closures-u4p0pq?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.26. What is callback() function in javascript?

A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.

```js
// callback() function

function greeting(name) {
  alert('Hello ' + name);
}

function processUserInput(callback) {
  var name = prompt('Please enter your name:');
  callback(name);
}

processUserInput(greeting);
```

The above example is a synchronous callback, as it is executed immediately.

*Note: callbacks are often used to continue code execution after an asynchronous operation has completed — these are called asynchronous callbacks.*.

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-callback-lz1qhw?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.27. How to avoid callback hell in javascript?

**Callback hell** is a phenomenon that afflicts a JavaScript developer when he tries to execute multiple asynchronous operations one after the other. Some people call it to be the **pyramid of doom**.  

**Example:**

```js
doSomething(param1, param2, function(err, paramx){
    doMore(paramx, function(err, result){
        insertRow(result, function(err){
            yetAnotherOperation(someparameter, function(s){
                somethingElse(function(x){
                });
            });
        });
    });
});
```

**Techniques for avoiding callback hell:**  

* Write comments
* Split functions into smaller functions
* Using Async.js
* Using Promises
* Using Async-Await

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.28. How do you encode an URL?

The encodeURI() function is used to encode complete URI which has special characters except (`,`, `/`, `?`, `:`, `@`, `&`, `=`, `+`, `$`, `#`) characters.

```js
var uri = 'https://mozilla.org/?x=шеллы';
var encoded = encodeURI(uri);

console.log(encoded); // https://mozilla.org/?x=%D1%88%D0%B5%D0%BB%D0%BB%D1%8B
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 9.29. How do you decode an URL?

The decodeURI() function is used to decode a Uniform Resource Identifier (URI) previously created by encodeURI().

```js
var uri = 'https://mozilla.org/?x=шеллы';
var encoded = encodeURI(uri);

console.log(encoded); // https://mozilla.org/?x=%D1%88%D0%B5%D0%BB%D0%BB%D1%8B
try {
  console.log(decodeURI(encoded)); // "https://mozilla.org/?x=шеллы"
} catch(e) { // catches a malformed URI
  console.error(e);
}
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>
