## # 7. ARRAY

<br/>

## Q 7.1. Explain arrays in JavaScript?

JavaScript array is an object that represents a collection of similar type of elements. It can holds values (of any type) not particularly in named properties/keys, but rather in numerically indexed positions.

**Syntax:**

```js
const array_name = [item-1, item-2, item-3, ...];    
```

**Example 01:** Creating an array

```js
// array of numbers
const numbers = [10, 20, 30, 40, 50];

// using new keyword
const numbers = new Array(10, 20, 30, 40, 50);

// array of strings
let fruits = ["Apple", "Orange", "Plum", "Mango"];
```

**Example 02:** Accessing array elements

```js
let fruits = ["Apple", "Orange", "Plum", "Mango"];

fruits[0]; // Apple
fruits[fruits.length - 1] // Mango

// Iterate array elements
for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
```

**Example 03:** Adding new array elements

```js
let fruits = ["Apple", "Orange", "Plum", "Mango"];

fruits.push("Grapes");  // Adds a new element (Grapes) to fruits
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-array-y73m66?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 7.2. What are associative arrays in javascript?

Associative arrays are basically objects in JavaScript where indexes are replaced by user-defined keys. They do not have a length property like a normal array and cannot be traversed using a normal for loop.

**Syntax:**

```js
const array_name = { key1: 'value1', key2: 'value2', key3: 'value3' }   
```

**Example:**

```js
const employee = {
  id: 12345,
  name: "Sakshi Memon",
  email: "sakshi.memon@email.com"
};

// Accesing employee elements
console.log(employee.id); // 12345
console.log(employee.name); // Sakshi Memon

// Array Length 
console.log(Object.keys(employee).length); // 3

// Retrieve the elements
for (let key in employee) {
  console.log(key + " = " + employee[key]);
}

// Output
id = 12345 
name = Sakshi Memon 
email = sakshi.memon@email.com 
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-associative-arrays-vxc4qc?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 7.3. Calculate the length of the associative array?

**Method 1:** Using `Object.keys().length`

```js
const employee = {
  id: 12345,
  name: "Sakshi Memon",
  email: "sakshi.memon@email.com"
};

console.log(Object.keys(employee).length); // Output 3
```

**Method 2:** Using `Object.hasOwnProperty()`

```js
function getLength(object) {
  let count = 0;
  for (let key in object) {
    // hasOwnProperty method check own property of object
    if (object.hasOwnProperty(key)) count++;
  }
  return count;
}

console.log(getLength(employee)); // Output 3
```

**Method 3:** Using `Object.getOwnPropertyNames()`

```js
const employee = {
  id: 12345,
  name: "Sakshi Memon",
  email: "sakshi.memon@email.com"
};

Object.getOwnPropertyNames(employee).length; // Output 3
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-associative-arrays-qye2t1?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 7.4. What is the difference between Array and Array of Objects in JavaScript?

Objects represent a special data type that is mutable and can be used to store a collection of data (rather than just a single value). Arrays are a special type of variable that is also mutable and can also be used to store a list of values.

**Example:** Arrays

```js
const numbers = [10, 20, 30];

// Iterating through loop
for (let i = 0; i < numbers.length; i++) {
  console.log(numbers[i]);
}

// Pop an element from array
numbers.pop();
console.log("after pop(): " + numbers);
```

**Example:** Array of Objects

```js
const employees = [
  { id: 101, name: "Sakshi Memon", email: "sakshi.memon@email.com" },
  { id: 102, name: "Subhash Shukla", email: "subhash.shukla@email.com" },
  { id: 103, name: "Mohini Karpe", email: "mohini.karpe@email.com" }
];

// Using DOT notation
console.log(employees[0].name);

// Using delete keyword
delete employees[0];

// Iterating using for..in loop
for (let key in employees) {
  console.log(employees[key]);
}
```

**Difference:**

|S.No.  | Array   | Array of objects |
|-------|---------|------------------|
|1.	|Arrays are best to use when the elements are numbers.|	Objects are best to use when the elements strings |
|3.	|The elements can be manipulated using []. | The properties can be manipulated using both . ( DOT ) notation and [].|
|4.	|The elements can be popped out of an array using the pop() function.| The keys or properties can be deleted by using the delete keyword.|
|5.	|Iterating through an array is possible using For loop, For..in, For..of, and ForEach().| Iterating through an array of objects is possible using For..in, For..of, and ForEach().|

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-array-vs-object-w7wz7i?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 7.5. Explain array methods [ join(), pop(), push(), shift(), unshift(), concat(), map(), filter(), reduce(), reduceRight(), every(), some(), indexOf(), lastIndexOf(), find(), findIndex(), includes() ]

**1. array.join()**:

The `join()` method creates and returns a new string by concatenating all of the elements in an array (or an array-like object), separated by commas or a specified separator string. If the array has only one item, then that item will be returned without using the separator.

```js
var elements = ['Fire', 'Air', 'Water'];

console.log(elements.join()); // Output: "Fire,Air,Water"
console.log(elements.join('')); // Output: "FireAirWater"
console.log(elements.join('-')); // Output: "Fire-Air-Water"
```

**2. array.pop()**:

The pop() method removes the last element from an array and returns that element. This method changes the length of the array.

```js
var plants = ['broccoli', 'cauliflower', 'kale'];

console.log(plants.pop()); // Output: "kale"
console.log(plants); // Output: Array ["broccoli", "cauliflower"]
console.log(plants.pop()); // Output: "cauliflower"
console.log(plants.pop()); // Output: "broccoli"
console.log(plants.pop()); // Output: "undefined"
```

**3. array.push()**:

The push() method adds one or more elements to the end of an array and returns the new length of the array.

```js
const animals = ['pigs', 'goats', 'sheep'];

const count = animals.push('cows');
console.log(count); // Output: 4
console.log(animals); // Output: Array ["pigs", "goats", "sheep", "cows"]
```

**4. array.shift()**:

The shift() method removes the first element from an array and returns that removed element. This method 
changes the length of the array.

```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.shift();
console.log(fruits) // Output: Array ["Orange", "Apple", "Mango"]
```

**5. array.unshift()**:

The unshift() method adds one or more elements to the beginning of an array and returns the new length of the array.

```js
var fruits = ["Banana", "Orange", "Apple"];
fruits.unshift("Mango","Pineapple");
console.log(fruits); // Output: Array ["Mango", "Pineapple", "Banana", "Orange", "Apple"]
```

**6. array.concat()**:

The concat() method is used to merge two or more arrays. This method does not change the existing arrays, but instead returns a new array.

```js
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];

console.log(array1.concat(array2)); // Output: Array ["a", "b", "c", "d", "e", "f"]
```

**7. array.map()**:

The map() method creates a new array with the results of calling a provided function on every element in the calling array.

```js
var array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map(x => x * 2); 

console.log(map1); // Output: Array [2, 8, 18, 32]
```

**8. array.filter()**:

The filter() method creates a new array with all elements that pass the test implemented by the provided function.

```js
var words = ['spray', 'limit', 'elite', 'exuberant', 'destruction'];

const result = words.filter(word => word.length > 6);

console.log(result); // Output: Array ["exuberant", "destruction"]
```

**9. array.reduce()**:

The reduce() method executes a reducer function (that you provide) on each element of the array, 
resulting in a single output value.

```js
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;

console.log(array1.reduce(reducer)); // Output: 10
console.log(array1.reduce(reducer, 5)); // Output: 15
```

**10. array.reduceRight()**:

The reduceRight() method applies a function against an accumulator and each value of the array (from right-to-left) to reduce it to a single value.

```js
const array1 = [[0, 1], [2, 3], [4, 5]].reduceRight(
  (accumulator, currentValue) => accumulator.concat(currentValue)
);

console.log(array1); // Output: Array [4, 5, 2, 3, 0, 1]
```

**11. array.every()**:

The every() method tests whether all elements in the array pass the test implemented by the provided function. It returns a Boolean value. 

```js
function isBelowThreshold(currentValue) {
  return currentValue < 40;
}

var array1 = [1, 30, 39, 29, 10, 13];
console.log(array1.every(isBelowThreshold)); // Output: true
```

**12. array.some()**:

The some() method tests whether at least one element in the array passes the test implemented by the provided function. It returns a Boolean value.

```js
var array = [1, 2, 3, 4, 5];

var even = function(element) {
  // checks whether an element is even
  return element % 2 === 0;
};

console.log(array.some(even)); // Output: true
```

**13. array.indexOf()**:

The indexOf() method returns the first index at which a given element can be found in the array, or -1 if it is not present.

```js
var beasts = ['ant', 'bison', 'camel'];

console.log(beasts.indexOf('camel')); // Output: 2
console.log(beasts.indexOf('giraffe')); // Output: -1
```

**14. array.lastIndexOf()**:

The lastIndexOf() method returns the index within the calling String object of the last occurrence 
of the specified value, searching backwards from fromIndex. Returns -1 if the value is not found.

```js
var paragraph = 'The quick brown fox jumps over the lazy dog. If the dog barked, was it really lazy?';

var searchTerm = 'dog';

console.log('The index of the first "' + searchTerm + '" from the end is ' + paragraph.lastIndexOf(searchTerm));
// Output: "The index of the first "dog" from the end is 52"
```

**15. array.find()**:

The find() method returns the value of the first element in the provided array that satisfies the provided testing function.

```js
var array1 = [5, 12, 8, 130, 44];

var found = array1.find(function(element) {
  return element > 100;
});

console.log(found); // Output: 130
```

**16. array.findIndex()**:

The findIndex() method returns the index of the first element in the array that satisfies the provided testing function. Otherwise, it returns -1, indicating that no element passed the test.

```js
var array1 = [5, 12, 8, 130, 44];

function isLargeNumber(element) {
  return element > 20;
}

console.log(array1.findIndex(isLargeNumber)); // Output: 3
```

**17. array.includes()**:

The includes() method determines whether an array includes a certain value among its entries, returning true or false as appropriate.

```js
var array1 = [1, 2, 3];
console.log(array1.includes(2)); // Output: true

var pets = ['cat', 'dog', 'bat'];
console.log(pets.includes('at')); // Output: false
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 7.6. What are the benefits of using spread syntax and how is it different from rest syntax?

Spread operator or Spread Syntax allow us to expand the arrays and objects into elements in the case of an array and key-value pairs in the case of an object.

**Example:**

```js
function sum(x, y, z) {
  return x + y + z;
}

const numbers = [1, 2, 3];
console.log(sum(...numbers));

// ES-5 way
console.log(sum.apply(null, numbers));
```

**Example:** Merge arrays

```js
const newBrands = ["Tesla", "Mahindra"];
const brands = ["Ford", "Honda", ...newBrands, "BMW"];

console.log(brands);
```

**Example:** Copy array/object

```js
let obj = { a: 10, b: 20, c: 30 };

// spread the object into a list of parameters
let objCopy = { ...obj };

// add new
obj.d = 40;

console.log(JSON.stringify(obj)); // { "a":10, "b":20, "c":30, "d":40 }
console.log(JSON.stringify(objCopy)); // { "a":10, "b":20, "c":30 }
```

**Difference:**

The main difference between `rest` and `spread` is that the rest operator puts the rest of some specific user-supplied values into a JavaScript array. But the spread syntax expands iterables into individual elements.

|Spread Syntax           |  Rest Syntax                    |
|------------------------|---------------------------------|
|Spread operator as its name suggests it spreads or expands the content of the given element.| Rest Syntax is just the opposite of spread syntax it collects the data and stores that data in a variable which we can use further in our code.|
|It expands an Array in form of elements, while in key-value pairs in the case of Objects. | It collects the data in the developer's desired format.|
|You may or may not use the strict mode inside the function containing the spread operator. | You can not use the strict mode inside function containing the rest operator.|
|It will overwrite the identical properties inside two objects and replace the former with the latter. | It simply collects all properties and wraps them inside a container.|

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-spread-vs-spread-qvxkkz?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 7.7. What is the difference between for..in and for..of?

Both `for..of` and `for..in` statements iterate over lists; the values iterated on are different though, `for..in` returns a **list of keys** on the object being iterated, whereas `for..of` returns a **list of values** of the numeric properties of the object being iterated.  

* **for in**: iterates over all enumerable properties of an object that are **keyed** by strings.  
* **for of**: iterates over the **values** of an iterable objects. including: built-in `String`, `Array`, array-like objects (e.g., `arguments` or `NodeList`), `TypedArray`, `Map`, `Set`, and `user-defined` iterables.

**Example:**

```js
// for..in
const list = [10, 20, 30];

for (let i in list) {
  console.log(i); // "0", "1", "2",
}

// for..of
for (let i of list) {
  console.log(i); // "10", "20", "30"
}
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-for-in-for-of-b0vn3v?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 7.8. Can you give an example for destructuring an array?

Destructuring is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables. That is, we can extract data from arrays and objects and assign them to variables.

```js
// Variable assignment.
const numbers = [10, 20, 30];
const [one, two, three] = numbers;

console.log(one); // 10
console.log(two); // 20
console.log(three); // 30
```

```js
// Swapping variables
let a = 100;
let b = 200;

[a, b] = [b, a];

console.log(a); // 20
console.log(b); // 10
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-array-destructure-bg71je?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 7.9. What are default values in destructuring assignment?

A variable can be assigned a default value when the value unpacked from the array or object is undefined during destructuring assignment. It helps to avoid setting default values separately for each assignment.  

**Array Destructuring:**

```js
const [x = 2, y = 4, z = 6] = [10];

console.log("x: " + x); // 10
console.log("y: " + y); // 4
console.log("z: " + z); // 6
```

**Object Destructuring:**

```js
const { i = 2, j = 4, k = 6 } = { n: 10 };

console.log("i: " + i); // 10
console.log("j: " + j); // 4
console.log("k: " + k); // 6
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/ecstatic-drake-iq971p?file=/src/index.js)**

## Q 7.10. When to use reduce(), map(), foreach() and filter() in JavaScript?

**1. forEach():**  

It takes a callback function and run that callback function on each element of array one by one.
Basically forEach works as a traditional for loop looping over the array and providing array elements to do operations on them.

```js
let numbers = [10, 20, 30];

numbers.forEach(function (number, index) {
  console.log(number + " comes at " + index);
});

// Output
10 comes at 0
20 comes at 1
30 comes at 2
```

**2. filter():**

The main difference between forEach() and filter() is that forEach just loop over the array and executes the callback but filter executes the callback and check its return value. If the value is true element remains in the resulting array but if the return value is false the element will be removed for the resulting array.

*Note: filter does not update the existing array it will return a new filtered array every time*.

```js
let numbers = [10, 20, 30];

let result = numbers.filter(function (number) {
  return number !== 20;
});

console.log(result);

// Output
[10, 30]
```

**3. map():**

map() like filter() & forEach() takes a callback and run it against every element on the array but whats makes it unique is it generate a new array based on your existing array.

Like filter(), map() also returns an array. The provided callback to map modifies the array elements and save them into the new array upon completion that array get returned as the mapped array.

```js
let numbers = [10, 20, 30];

let mapped = numbers.map(function (number) {
  return number * 10;
});

console.log(mapped);

// Output
[100, 200, 300]
```

**4. reduce():**

reduce() method of the array object is used to reduce the array to one single value.

```js
let numbers = [10, 20, 30];

let sum = numbers.reduce(function (sum, number) {
  return sum + number;
});

console.log(sum); // Output: 60
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-loop-m755cw?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 7.11. How do you define JSON arrays?

JSON is an acronym for JavaScript Object Notation, and is "an open standard data interchange format".

JSON array represents ordered list of values. JSON array can store multiple values. It can store string, number, boolean or object in JSON array.

```js
// Empty JSON array
const empty = [ ];


// JSON Array of Numbers
const numbers = [12, 34, 56, 43, 95];


// JSON Array of Objects
{
 "employees": [
   { "name": "Kabir Dixit", "email": "kabir.dixit@gmail.com", "age": 23 },
   { "name": "Mukta Bhagat", "email": "mukta.bhagat@gmail.com", "age": 28 },
   { "name": "Sakshi Ramakrishnan", "email": "sakshi.ramakrishnan@gmail.com", "age": 33 }
  ]
}

// access array values
console.log(employees[0].name) // Kabir Dixit
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 7.12. How to validate JSON Object in javascript?

`JSON.parse()` function will use string and converts to JSON object and if it parses invalidate JSON data, it throws an exception ( **Uncaught SyntaxError: Unexpected string in JSON** ).

```js
function isValidJson(json) {
  try {
    JSON.parse(json);
    return true;
  } catch (e) {
    return false;
  }
}

console.log(isValidJson("{}")); // true
console.log(isValidJson("abc")); // false
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-validate-json-iwzom7?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 7.13. What is the purpose JSON stringify?

When sending data to a web server, the data has to be in a string format. The `JSON.stringify()` method converts a JavaScript object or value to a JSON string format.

```js
const user = {'name': 'Shashi Meda', 'email': 'shashi.meda@email.com', 'age': 28}

console.log(JSON.stringify(user)); // {"name":"Shashi Meda","email":"shashi.meda@email.com","age":28}
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 7.14. How do you parse JSON string?

When receiving the data from a web server, the data is always in a string format. But you can convert this string value to javascript object using `JSON.parse()` method.

```js
const user = '{"name": "Shashi Meda", "email": "shashi.meda@email.com", "age": 28}'

console.log(JSON.parse(user));// {'name': 'Shashi Meda', 'email': 'shashi.meda@email.com', 'age': 28}
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 7.15. What is the purpose of compare function while sorting arrays?

The purpose of the compare function is to define an alternative sort order. When the `sort()` function compares two values, it sends the values to the compare function, and sorts the values according to the returned (negative, zero, positive) value.

If omitted, the array elements are converted to strings, then sorted according to each character's Unicode code point value.

```js
const numbers = [1, 2, 5, 3, 4];

numbers.sort((a, b) => b - a);
console.log(numbers); // [5, 4, 3, 2, 1]
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-sort-ykfhck?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 7.16. Can you describe the main difference between a `.forEach` loop and a `.map()` loop and why you would pick one versus the other?

To understand the differences between the two, Let us look at what each function does.

**1. Array.forEach():**

* Iterates through the elements in an array.
* Executes a callback for each element.
* Does not return a value.

```js
const numbers = [10, 20, 30];
const doubled = numbers.forEach((num, index) => {
  return num * 2;
});

console.log(doubled) // undefined
```

**2. Array.map():**

* Iterates through the elements in an array.
* "Maps" each element to a new element by calling the function on each element, creating a new array as a result.

```js
const numbers = [10, 20, 30];
const doubled = numbers.map(num => {
  return num * 2;
});

console.log(doubled) // [20, 40, 60]
```

The main difference between `.forEach` and `.map()` is that `.map()` returns a new array. If you need the result, but do not wish to mutate the original array, `.map()` is the clear choice. If you simply need to iterate over an array, `forEach` is a fine choice.

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-foreach-vs-map-kxch52?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 7.17. What is unshift() method in JavaScript?

The `unshift()` method adds one or more elements to the beginning of an array and returns the new length of the array.

**Example:**

```js
const numbers = [10, 20, 30];

console.log(numbers.unshift(40, 50)); // 5
console.log(numbers); // [40, 50, 10, 20, 30]
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-unshift-khl0dq?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 7.18. What is a rest parameter?

The rest parameter is used to represent an indefinite number of arguments as an array. The important point here is only the function\'s last parameter can be a "rest parameter".

This feature has been introduced to reduce the boilerplate code that was induced by the arguments.

**Example:**

```js
function sum(...args) {
  return args.reduce((previous, current) => {
    return previous + current;
  });
}

console.log(sum(10)); // 10
console.log(sum(10, 20)); // 30
console.log(sum(10, 20, 30)); // 60
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-rest-parameters-w8zy28?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 7.19. What happens if you do not use rest parameter as a last argument?

The rest parameter should be the last argument, as its job is to collect all the remaining arguments into an array.

**Example:** If you define a function like below it does not make any sense and will throw an `SyntaxError`.

```js
function display(a, ...args, b) {
  console.log(a);
  for (let i = 0; i < args.length; i++) {
    console.log(args[i]);
  }
  console.log(b);
}

display(10, 20, 30, 40, 50);

// Output
SyntaxError: Rest element must be last element
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-rest-parameter-v8r5yt?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>
