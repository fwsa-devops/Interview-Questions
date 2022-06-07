## # 11. OBJECTS

<br/>

## Q 11.1. What are the possible ways to create objects in JavaScript?

**1. Object Constructor**:

The simpliest way to create an empty object is using Object constructor. Currently this approach is not recommended.

```js
let object = new Object();
```

**2. Object create method**:

The create method of Object creates a new object by passing the prototype object as a parameter

```js
let object = Object.create(null);
```

**3. Object Literal**:

The object literal syntax is equivalent to create method when it passes `null` as parameter

```js
let person = {};
```

**4. Function Constructor**:

Create any function and apply the new operator to create object instances,

```js
function Person(name) {
 let object = {};
 object.name = name;
 object.age = 26;

 return object;
}

let person = new Person("Alex");
```

**5. Function Constructor with prototype**:

This is similar to function constructor but it uses prototype for their properties and methods,

```js
function Person(){}

Person.prototype.name = "Alex";
let person = new Person();
```

**6. ES6 Class**:

ES6 introduces class feature to create the objects

```js
class Person {
 constructor(name) {
    this.name = name;
 }
}

let person = new Person("Alex");
```

**7. Singleton Pattern**:

A Singleton is an object which can only be instantiated one time. Repeated calls to its constructor return the same instance and this way one can ensure that they don\'t accidentally create multiple instances.

```js
let object = new function() {
  this.name = "Alex";
}
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.2. What are the recommendations to create new object?

It is recommended to avoid creating new objects using `new Object()`. Instead you can initialize values based on it is type to create the objects.

* Assign {} instead of new Object()
* Assign "" instead of new String()
* Assign 0 instead of new Number()
* Assign false instead of new Boolean()
* Assign [] instead of new Array()
* Assign /()/ instead of new RegExp()
* Assign function (){} instead of new Function()

**Example:**

```js
let obj1 = {};
let obj2 = "";
let obj3 = 0;
let obj4 = false;
let obj5 = [];
let obj6 = /()/;
let obj7 = function(){};
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.3. What are the different ways to access object properties?

There are 3 possible ways for accessing the property of an object.

**1. Dot notation:** It uses dot for accessing the properties

```js
objectName.property
```

**2. Square brackets notation:** It uses square brackets for property access

```js
objectName["property"]
```

**3. Expression notation:** It uses expression in the square brackets

```js
objectName[expression]
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.4. How to check if an object is an array or not?

The `Array.isArray()` method determines whether an object is an array. This function returns `true` if the object is an array, and `false` if not.

```js
 // Creating some variables
  var v1 = {name: "John", age: 22};   
  var v2 = ["red", "green", "blue", "yellow"];
  var v3 = [10, 20, 30, 40, 50];
  var v4 = null;
  
  // Testing the variables data type
  typeof(v1); // Returns: "object"
  typeof(v2); // Returns: "object"
  typeof(v3); // Returns: "object"
  typeof(v3); // Returns: "object"
  
  // Testing if the variable is an array
  Array.isArray(v1);  // Returns: false
  Array.isArray(v2);  // Returns: true
  Array.isArray(v3);  // Returns: true
  Array.isArray(v4);  // Returns: false
```

*Note: The `Array.isArray()` method is supported in all major browsers, such as Chrome, Firefox, IE (9 and above)*

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.5. Can you give an example for destructuring an object?

Destructuring is an expression available in ES6 which enables a succinct and convenient way to extract values of Objects or Arrays and place them into distinct variables.

**Example:**

```js
// Object Destructuring

let person = { name: "Sarah", country: "India", job: "Developer" };

let name = person.name;
let country = person.country;
let job = person.job;

console.log(name); // Sarah
console.log(country); // India
console.log(job); // Developer
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-object-destructuring-xg7q51?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.6. How do you clone an object in JavaScript?

Using the object spread operator `...`, the object own enumerable properties can be copied into the new object. This creates a shallow clone of the object.

```js
const obj = { a: 10, b: 20 }
const shallowClone = { ...obj }
```

With this technique, prototypes are ignored. In addition, nested objects are not cloned, but rather their references get copied, so nested objects still refer to the same objects as the original.

**Example 01**: Clone the Object Using Object.assign()

```js
const person = {
    name: 'John',
    age: 21,
}

// cloning the object
const clonePerson = Object.assign({}, person);

console.log(clonePerson);

// changing the value of clonePerson
clonePerson.name = 'Peter';

console.log(clonePerson.name);
console.log(person.name);


// Output
{name: "John", age: 21}
Peter
John
```

**Example 02**: Clone the Object Using Spread Syntax

```js
const person = {
    name: 'John',
    age: 21,
}

// cloning the object
const clonePerson = { ... person}

console.log(clonePerson);

// changing the value of clonePerson
clonePerson.name = 'Peter';

console.log(clonePerson.name);
console.log(person.name);


// Output
{name: "John", age: 21}
Peter
John
```

**Example 03**: Clone the Object Using JSON.parse()

```js
const person = {
    name: 'John',
    age: 21,
}

// cloning the object
const clonePerson = JSON.parse(JSON.stringify(person));

console.log(clonePerson);

// changing the value of clonePerson
clonePerson.name = 'Peter';

console.log(clonePerson.name);
console.log(person.name);

// Output
{name: "John", age: 21}
Peter
John
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-object-clone-hj5uhr?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.7. How do you copy properties from one object to other?

You can use `Object.assign()` method which is used to copy the values and properties from one or more source objects to a target object.  It returns the target object which has properties and values copied from the target object. The syntax would be as below,

```js
Object.assign(target, ...sources)
```

Let us take example with one source and one target object,

```js
const target = { a: 1, b: 2 };
const source = { b: 3, c: 4 };

const returnedTarget = Object.assign(target, source);

console.log(target); // { a: 1, b: 3, c: 5 }
console.log(returnedTarget); // { a: 1, b: 3, c: 5 }
```

As observed in the above code, there is a common property(`b`) from source to target so it is value is been overwritten.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.8. What is the difference between native, host and user objects?

**1. Native Objects**:

Are objects that are part of the JavaScript language defined by the ECMAScript specification. For example, `String`, `Math`, `RegExp`, `Object`, `Function` etc core objects defined in the ECMAScript spec.

**2. Host Objects**:

Are objects provided by the browser or runtime environment (Node). For example, `window`, `XmlHttpRequest`, `DOM nodes` etc considered as host objects.

**3. User Objects**:

Are objects defined in the javascript code. For example, User object created for profile information.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.9. What are the properties of Intl object?

The `Intl` object is the namespace for the ECMAScript Internationalization API that provides language number formatting, string comparison, and date/time formatting.

Below are the list of properties available on Intl object,

**1. Collator:**

Intl.Collator provides a language-aware comparison of Strings for sorting and searching.

**Example:**

```js
// Intl.Collator()

let collatorEs = new Intl.Collator("es").compare;
console.log(["a", "z", "ñ", "b"].sort(collatorEs)); // ["a", "b", "ñ", "z"]


let collatorEsCaseFirts = new Intl.Collator("es", { caseFirst: "upper" }).compare;  
console.log(["a", "A", "z", "ñ", "b"].sort(collatorEsCaseFirts)); // ["A", "a", "b", "ñ", "z"]
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-intl-collator-jusk3c?file=/src/index.js)**

**2. DateTimeFormat:**

These are the objects that enable language-sensitive date and time formatting.

**Example:**

```js
// Intl.DateTimeFormat()

let now = new Date();
let nowEnUs = new Intl.DateTimeFormat("en-US");
let noeEs = new Intl.DateTimeFormat("es-ES");

console.log(nowEnUs.format(now)); // 5/17/2022 
console.log(noeEs.format(now)); // 17/5/2022 
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-intl-datetimeformat-mnvt4u?file=/src/index.js)**

**3. ListFormat:**

These are the objects that enable language-sensitive list formatting.

**Example:**

```js
// Intl.ListFormat()

let lfEn = new Intl.ListFormat("en", {
    localeMatcher: "lookup",
    type: "disjunction",
    style: "narrow"
});
console.log(lfEn.format(['Hannibal smith', 'Murdock' , 'Faceman', 'B.A." Baracus']));
// Hannibal smith, Murdock, Faceman, or B.A." Baracus

let lfEs = new Intl.ListFormat("es", {
    localeMatcher: "lookup",
    type: "disjunction",
    style: "narrow"
});
console.log(lfEs.format(['Hannibal smith', 'Murdock' , 'Faceman', 'B.A." Baracus']));
// Hannibal smith, Murdock, Faceman o B.A." Baracus
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-intl-listformat-4dq79u?file=/src/index.js)**

**4. NumberFormat:**

Objects that enable language-sensitive number formatting.

```js
// Intl.NumberFormat()

let myNumber = 1000000.999;
let nfEs = new Intl.NumberFormat('es-ES');
let nfEn = new Intl.NumberFormat('en-EU');

console.log(nfEs.format(myNumber)); //1.000.000,999

console.log(nfEn.format(myNumber)); // 1,000,000.999
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-intl-numberformat-whhvc9?file=/src/index.js)**

**5. RelativeTimeFormat:**

Objects that enable language-sensitive relative time formatting.

**Example:**

```js
// Intl.RelativeTimeFormat()

let rtfEn = new Intl.RelativeTimeFormat('en', { numeric: 'auto'  });

console.log(rtfEn.format(2, 'day')); // in 2 days
console.log(rtfEn.format(-1, 'day')); // yesterday
console.log(rtfEn.format(-5, 'month')); //5 months ago


let rtfEs = new Intl.RelativeTimeFormat('es', { numeric: 'auto' });

console.log(rtfEs.format(2, 'day')); // pasado mañana
console.log(rtfEs.format(-1, 'day')); // ayer
console.log(rtfEs.format(-5, 'month')); // Hace 5 meses
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-intl-relativetimeformat-cxwko6?file=/src/index.js)**

**6. Locale:**

Intl.Locale has a toString method that represents the complete contents of the locale. This method allows Locale instances to be provided as an argument to existing Intl constructors.

**Example:**

```js
// Example: Intl.Locale()

let newLocale = new Intl.Locale("en-US", { language: "es" });
console.log(newLocale.toString()); // es-US

let now = new Date();
let dtfMyNewLocale = new Intl.DateTimeFormat(newLocale);

console.log(dtfMyNewLocale.format(now)); // 17/5/2022 


let newLocale2 = new Intl.Locale("en-US", { language: "en" });
console.log(newLocale2.toString()); //en-US

let now2 = new Date();
let dtfMyNewLocale2 = new Intl.DateTimeFormat(newLocale2);

console.log(dtfMyNewLocale2.format(now2)); // 5/17/2022 
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-intl-locale-dgel2y?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.10. How do you convert date to another timezone in javascript?

The `.toLocaleString()` method to convert date in one timezone to another. 

For example, let us convert current date to British English timezone as below,

```js
console.log(event.toLocaleString('en-GB', { timeZone: 'UTC' })); //29/06/2019, 09:56:00
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.11. Explain the difference between mutable and immutable objects?

A mutable object is an object whose state can be modified after it is created. An immutable object is an object whose state cannot be modified after it is created.

In JavaScript numbers, strings, null, undefined and Booleans are primitive types which are immutable. Objects, arrays, functions, classes, maps, and sets are mutable.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.12. How to create immutable object in javascript

In JavaScript, some built-in types (numbers, strings) are immutable, but custom objects are generally mutable. Some built-in immutable JavaScript objects are `Math`, `Date`.

Here are a few ways to add/simulate immutability on plain JavaScript objects.

**1. Object Constant Properties:**

By combining `writable: false` and `configurable: false`, you can essentially create a constant (cannot be changed, redefined or deleted) as an object property, like:

**Example:**

```js
let myObject = {};

Object.defineProperty(myObject, 'number', {
  value: 10,
  writable: false,
  configurable: false,
});

console.log(myObject.number); // 10  
myObject.number = 20;          
console.log(myObject.number); // 10
```

**2. Prevent Extensions:**

This method prevents the addition of new properties to our existing object. `preventExtensions()` is a irreversible operation. We can never add extra properties to the object again.

**Example:**

```js
const myCar = {
  maxSpeed: 250,
  batteryLife: 300,
  weight: 123
};

Object.isExtensible(myCar); // true
Object.preventExtensions(myCar);

Object.isExtensible(myCar); // false
myCar.color = 'blue';
console.log(myCar.color) // undefined
```

**3. Seal:**

It prevents additions or deletion of properties. `seal()` also prevents the modification of property descriptors.

**Example:**

```js
const myCar = {
  maxSpeed: 250,
  batteryLife: 300,
  weight: 123
};

Object.isSealed(myCar); // false
Object.seal(myCar);
Object.isSealed(myCar); // true

myCar.color = 'blue';
console.log(myCar.color); // undefined

delete myCar.batteryLife; // false
console.log(myCar.batteryLife); // 300

Object.defineProperty(myCar, 'batteryLife'); // TypeError: Cannot redefine property: batteryLife
```

**4. Freeze:**

It does the same that `Object.seal()` plus it makes the properties non-writable.

**Example:**

```js
const myCar = {
  maxSpeed: 250,
  batteryLife: 300,
  weight: 123
};

Object.isFrozen(myCar); // false
Object.freeze(myCar);
Object.isFrozen(myCar); // true

myCar.color = 'blue';
console.log(myCar.color); // undefined

delete myCar.batteryLife;
console.log(myCar.batteryLife); // 300

Object.defineProperty(myCar, 'batteryLife'); // TypeError: Cannot redefine property: batteryLife

myCar.batteryLife = 400;
console.log(myCar.batteryLife); // 300
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.13. How do you determine whether object is frozen or not?

`Object.isFrozen()` method is used to determine if an object is frozen or not. An object is frozen if all of the below conditions hold true,

1. If it is not extensible.
2. If all of its properties are non-configurable.
3. If all its data properties are non-writable.
The usage is going to be as follows,

```js
const object = {
  property: 'Welcome JS world'
};
Object.freeze(object);
console.log(Object.isFrozen(object));
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.14. How can you achieve immutability in your own code?

For "mutating" objects, use the spread operator, `Object.assign`, `Array.concat()`, etc., to create new objects instead of mutate the original object.

**Example:**

```js
// Array Example
const arr = [10, 20, 30];
const newArr = [...arr, 40, 50]; // [10, 20, 30, 40, 50]

// Object Example
const human = Object.freeze({ race: "human" });
const aditya = { ...human, name: "Aditya" }; // {race: "human", name: "Aditya"}
const alienAditya = { ...aditya, race: "alien" }; // {race: "alien", name: "Aditya"}
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-immutable-object-jty055?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.15. What is the drawback of declaring methods directly in JavaScript objects?

One of the drawback of declaring methods directly in JavaScript objects is that they are very memory inefficient.  When you do that, a new copy of the method is created for each instance of an object.

**Example:**

```js
const Employee = function (name, company, salary) 
{
  this.name = name || "";
  this.company = company || "";
  this.salary = salary || 5000;

  // We can create a method like this:
  this.formatSalary = function () {
    return "$ " + this.salary;
  };
};

// we can also create method in Employee's prototype:
Employee.prototype.formatSalary2 = function () {
  return "$ " + this.salary;
};

// Creating Objects
let emp1 = new Employee("Yuri Garagin", "Company 1", 1000);
let emp2 = new Employee("Dinesh Gupta", "Company 2", 2000);
```

Here, each instance variable `emp1`, `emp2` has own copy of `formatSalary` method. However the `formatSalary2` will only be added once to an object `Employee.prototype`.

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-class-object-96mc2r?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.16. How do you compare Object and Map?

**1. Object:**

A data structure in which data is stored as key value pairs. In an object the key has to be a number, string, or symbol. The value can be anything so also other objects, functions, etc. An object is a **nonordered** data structure, i.e. the sequence of insertion of key value pairs is not remembered.

**Example:**

```js
// Object() 

let obj = {};

// adding properties to a object
obj.prop = 10;
obj[2] = 20;

// getting nr of properties of the object
Object.keys(obj).length; // 2

// deleting a property
delete obj[2];

obj; // {prop: 10}
```

**2. ES6 Map:**

A data structure in which data is stored as key value pairs. In which **a unique key maps to a value**. Both the key and the value can be in **any data type**. A map is an iterable data structure. This means that the sequence of insertion is remembered and that we can access the elements in e.g. a `for..of` loop.

**Example:**

```js
// Map() 

const myMap = new Map();

const keyString = "a string",
  keyObj = {},
  keyFunc = function () {};

// setting the values
myMap.set(keyString, "value associated with 'a string'");
myMap.set(keyObj, "value associated with keyObj");
myMap.set(keyFunc, "value associated with keyFunc");

myMap.size; // 3

// getting the values
myMap.get(keyString); // "value associated with 'a string'"
myMap.get(keyObj); // "value associated with keyObj"
myMap.get(keyFunc); // "value associated with keyFunc"

myMap.get("a string"); // "value associated with 'a string'"
// because keyString === 'a string'
myMap.get({}); // undefined, because keyObj !== {}
myMap.get(function () {}); // undefined, because keyFunc !== function () {}
```

**Key differences:**

* A `Map` is ordered and iterable, whereas a objects is not ordered and not iterable
* We can put any type of data as a `Map` key, whereas objects can only have a number, string, or symbol as a key.
* A `Map` inherits from `Map.prototype`. This offers all sorts of utility functions and properties which makes working with `Map` objects a lot easier.

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-object-vs-map-iodiyv?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.17. What is shallow copy and deep copy in javascript?

**1. Shallow Copy:**

Shallow copy is a bit-wise copy of an object. A new object is created that has an exact copy of the values in the original object. If any of the fields of the object are references to other objects, just the reference addresses are copied i.e., only the memory address is copied.

A Shallow copy of the object can be done using `object.assign()`

**Example:**

```js
// Shallow Copy

let obj = {
  a: 10,
  b: 20,
};

let objCopy = Object.assign({}, obj);
console.log(objCopy); // Result - { a: 1, b: 2 }
```

**2. Deep Copy:**

A deep copy copies all fields, and makes copies of dynamically allocated memory pointed to by the fields. A deep copy occurs when an object is copied along with the objects to which it refers.

A Deep copy of the object can be done using `JSON.parse(JSON.stringify(object))`

**Example:**

```js
// Deep Copy

let obj2 = {
  a: 10,
  b: {
    c: 20
  }
};

let newObj = JSON.parse(JSON.stringify(obj2));
obj2.b.c = 30;

console.log(obj2); // { a: 10, b: { c: 20 } }
console.log(newObj); // { a: 10, b: { c: 20 } }
```

<p align="center">
  <img src="assets/deepcopy.png" alt="Shallow Copy and Deep Copy" />
</p>

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-shallow-vs-deep-copy-ik5b7h?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.18. Write a function called deepClone which takes an object and creates a object copy of it?

``` javascript
var newObject = deepClone(obj);
```

Solution:

```js
function deepClone(object) {
  var newObject = {};
  for (var key in object) {
    if (typeof object[key] === "object" && object[key] !== null) {
      newObject[key] = deepClone(object[key]);
    } else {
      newObject[key] = object[key];
    }
  }
  return newObject;
}
```

**Explanation:** We have been asked to do deep copy of object so What is basically It is mean ?. Let us understand in this way you have been given an object `personalDetail` this object contains some property which again a type of object here as you can see `address` is an object and `phoneNumber` in side an `address` is also an object. In simple term `personalDetail` is nested object(object inside object). So Here deep copy means we have to copy all the property of `personalDetail` object including nested object.

```js
var personalDetail = {
	name : 'Alex',
	address : {
	  location: 'xyz',
	  zip : '123456',
	  phoneNumber : {
	    homePhone: 8797912345,
	    workPhone : 1234509876
	  }
	}
}
```

So when we do deep clone then we should copy every property (including the nested object).

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.19. Write a function called `Clone` which takes an object and creates a object copy of it but not copy deep property of object?

```js
  var objectLit = {foo : 'Bar'};
	var cloneObj = Clone(obj); // Clone is the function which you have to write 
	console.log(cloneObj === Clone(objectLit)); // this should return false
	console.log(cloneObj == Clone(objectLit)); // this should return true
```

**solution:**

```js
function Clone(object){
  var newObject = {};
  for(var key in object){
  	newObject[key] = object[key];
  }
  return newObject;
}
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.20. How do you check if a key exists in an object?

**1. Using `in` operator:**

You can use the in operator whether a key exists in an object or not

```js
const obj = { key: undefined };

console.log("key" in obj); // true, regardless of the actual value
```

and If you want to check if a key doesn\'t exist, remember to use parenthesis,

```js
const obj = { not_key: undefined };

console.log(!("key" in obj)); // true if "key" doesn't exist in object
```

**2. Using `hasOwnProperty()` method:**

You can use `hasOwnProperty` to particularly test for properties of the object instance (and not inherited properties)

```js
const obj = { key: undefined };

console.log(obj.hasOwnProperty("key")); // true
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-in-operator-3fxd3h?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.21. How do you loop through or enumerate javascript object?

You can use the `for-in` loop to loop through javascript object. You can also make sure that the key you get is an actual property of an object, and doesn\'t come from the prototype using `hasOwnProperty` method.

```js
var object = {
    "k1": "value1",
    "k2": "value2",
    "k3": "value3"
};

for (var key in object) {
    if (object.hasOwnProperty(key)) {
        console.log(key + " -> " + object[key]); // k1 -> value1 ...
    }
}
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.22. How do you test for an empty object?

**a.) Using Object keys(ECMA 5+):** You can use object keys length along with constructor type.

```js
Object.keys(obj).length === 0 && obj.constructor === Object 
```

**b.) Using Object entries(ECMA 7+):** You can use object entries length along with constructor type.

```js
Object.entries(obj).length === 0 && obj.constructor === Object 
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.23. What is a proxy object?

The `Proxy` object allows to create an object that can be used in place of the original object, but which may redefine fundamental `Object` operations like getting, setting, and defining properties. 

Proxy objects are commonly used to log property accesses, validate, format, or sanitize inputs, and so on. 

**Syntax:**

```js
const proxy = new Proxy(target, handler)
```

In this syntax:

* **target**: is an object to wrap.
* **handler**:  is an object that contains methods to control the behaviors of the `target`.

**Example:**

```js
// define an object called user
const user = {
  firstName: "Aniket",
  lastName: "Narula",
  email: "aniket.narula@email.com"
};

// define a handler object:
const handler = {
  get(target, property) {
    console.log(`Property ${property} has been read.`);
    return target[property];
  }
};

// create a proxy object:
const proxyUser = new Proxy(user, handler);

console.log(proxyUser.firstName);
console.log(proxyUser.lastName);

// Output
Property firstName has been read.
Aniket
Property lastName has been read.
Narula

user.firstName = 'Sonam';
console.log(proxyUser.firstName);

// Output
Property firstName has been read.
Sonam
```

There are many real-world applications for Proxies

* Validation
* Value correction
* Property lookup extensions
* Tracing property accesses
* Revocable references
* Implementing the DOM in javascript

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-in-operator-3fxd3h?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.24. What is Reflection in JavaScript?

Reflection is defined as the ability of a program to inspect and modify its structure and behavior at runtime. `Reflect` is not a function object. `Reflect` helps with forwarding default operations from the handler to the target.

**Example:**

```js
// Math.max()
let number = Reflect.apply(Math.max, Math, [10, 20, 30]);
console.log(number); // 30

// FromCharCode()
let string = Reflect.apply(String.fromCharCode, undefined, [ 104, 101, 108, 108, 111]); // "hello"
console.log(string); // "hello"

// RegExp()
let index = Reflect.apply(RegExp.prototype.exec, /o/, ["Hello"]).index;
console.log(index); // 4
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-reflection-nwgjhg?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.25. How do you display the current date in javascript?

You can use `new Date()` to generate a new Date object containing the current date and time. 

**Example:**

```js
// Current Date

let today = new Date();
let dd = String(today.getDate()).padStart(2, '0');
let mm = String(today.getMonth() + 1).padStart(2, '0'); //January is 0!
let yyyy = today.getFullYear();

today = mm + '/' + dd + '/' + yyyy;
document.write(today);
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-date-nzwk0c?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.26. How do you add a key value pair in javascript?

There are two possible solutions to add new properties to an object. Let us take a simple object to explain these solutions.

```js
const object = {
    key1: value1,
    key2: value2
};
```

**a.) Using dot notation:** This solution is useful when you know the name of the property

```js
object.key3 = "value3";
```

**b.) Using square bracket notation:** This solution is useful when the name of the property is dynamically determined.

```js
obj["key3"] = "value3";
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.27. How do you check whether an object can be extendable or not?

The `Object.isExtensible()` method is used to determine if an object is extensible or not. i.e, Whether it can have new properties added to it or not.

```js
// Validate object is extendable or not

const person = {
  firstName: "Sima",
  lastName: "Chander",
  email: "sima.chander@email.com"
};
console.log(Object.isExtensible(person)); //true

Object.preventExtensions(person);
console.log(Object.isExtensible(person)); // false
```

*Note: By default, all the objects are extendable. i.e, The new properties can added or modified.*

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-isextensible-xz0ygi?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.28. How to compare two objects in javascript?

Objects are reference types so you can\'t just use `===` or `==` to compare 2 objects. One quick way to compare if 2 objects have the same key value, is using `JSON.stringify()`. Another way is using Lodash `.isEqual()` function.

**Example:**

```js
const obj1 = { id: 100 };
const obj2 = { id: 100 };

// Using JavaScript
JSON.stringify(obj1) === JSON.stringify(obj2); // true

// Using Lodash
_.isEqual(obj1, obj2); // true
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-object-comparison-w3o578?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.29. How do you get enumerable key and value pairs?

The `Object.entries()` method is used to return an array of a given object own enumerable string-keyed property [key, value] pairs, in the same order as that provided by a `for...in` loop. Let us see the functionality of object.entries() method in an example,

```js
const object = {
  a: 'Good morning',
  b: 100
};

for (let [key, value] of Object.entries(object)) {
  console.log(`${key}: ${value}`); // a: 'Good morning'
                                  // b: 100
}
```

*Note: The order is not guaranteed as object defined*.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.30. What is the main difference between Object.values and Object.entries method?

The `Object.values()` method\'s behavior is similar to `Object.entries()` method but it returns an array of values instead [key,value] pairs.

```js
const object = {
  a: 'Good morning',
  b: 100
};

for (let value of Object.values(object)) {
  console.log(`${value}`); // 'Good morning'
                                100
}
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.31. How can you get the list of keys of any object?

You can use `Object.keys()` method which is used return an array of a given object\'s own property names, in the same order as we get with a normal loop. For example, you can get the keys of a user object,

```js
const user = {
  name: 'John',
  gender: 'male',
  age: 40
};

console.log(Object.keys(user)); //['name', 'gender', 'age']
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 11.32. What is difference between array[] vs object()?

* `[]` is declaring an array.
* `{}` is declaring an object.

An array has all the features of an object with additional features (you can think of an array like a sub-class of an object) where additional methods and capabilities are added in the Array sub-class. In fact, typeof [] === "object" to further show you that an array is an object.

The additional features consist of a magic `.length` property that keeps track of the number of items in the array and a whole slew of methods for operating on the array such as `.push()`, `.pop()`, `.slice()`, `.splice()`, etc... You can see a list of array methods here.

An object gives you the ability to associate a property name with a value as in:

```js
var x = {};
x.foo = 3;
x["whatever"] = 10;
console.log(x.foo);      // shows 3
console.log(x.whatever); // shows 10
```

Object properties can be accessed either via the `x.foo` syntax or via the array-like syntax `x["foo"]`. The advantage of the latter syntax is that you can use a variable as the property name like `x[myvar]` and using the latter syntax, you can use property names that contain characters that Javascript won\'t allow in the `x.foo` syntax.

An array is an object so it has all the same capabilities of an object plus a bunch of additional features for managing an **ordered**, **sequential** list of numbered indexes starting from `0` and going up to some length. Arrays are typically used for an ordered list of items that are accessed by numerical index. And, because the array is ordered, there are lots of useful features to manage the order of the list `.sort()` or to add or remove things from the list.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>
