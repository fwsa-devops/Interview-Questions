  ## # 4. OPERATORS

<br/>

## Q 4.1. What are various operators supported by javascript?

An operator is capable of manipulating(mathematical and logical computations) a certain value or operand. There are various operators supported by JavaScript as below,

**Arithmetic Operators:**

Arithmetic operators are used to perform mathematical operations between numeric operands.

|Operators|Description             | Example ( say `let x = 10, y = 20;`) |
|--------|------------------------|-------------|
| +      |Adds two numeric operands.| x + y     |
| -      |Subtract right operand from left operand| y - x|
| *      |Multiply two numeric operands.| x * y|
| /      |Divide left operand by right operand.| y / x|
| %      |Modulus operator. Returns remainder of two operands.| x % 2|
| ++     |Increment operator. Increase operand value by one.| x++|
| --     |Decrement operator. Decrease value by one.| x--|

**Comparison Operators:**

JavaScript provides comparison operators that compare two operands and return a boolean value `true` or `false`.

|Operators|	Description|
|---------|-------------|
|==       |Compares the equality of two operands without considering type.|
|===      |Compares equality of two operands with type.|
|!=       |Compares inequality of two operands.|
|>        |Returns a boolean value true if the left-side value is greater than the right-side value; otherwise, returns false.|
|<        |Returns a boolean value true if the left-side value is less than the right-side value; otherwise, returns false.|
|>=       |Returns a boolean value true if the left-side value is greater than or equal to the right-side value; otherwise, returns false.|
|<=       |Returns a boolean value true if the left-side value is less than or equal to the right-side value; otherwise, returns false.|

**Logical Operators:**

The logical operators are used to combine two or more conditions.

|Operators |Description         |
|----------|--------------------|
|&&	&&     |is known as AND operator. It checks whether two operands are non-zero or not (0, false, undefined, null or "" are considered as zero). It returns 1 if they are non-zero; otherwise, returns 0.|
|<code>||</code> | <code>||</code> is known as OR operator. It checks whether any one of the two operands is non-zero or not (0, false, undefined, null or "" is considered as zero). It returns 1 if any one of of them is non-zero; otherwise, returns 0.|
|!         |	! is known as NOT operator. It reverses the boolean result of the operand (or condition). !false returns true, and !true returns false.|

**Assignment Operators:**

The assignment operators to assign values to variables with less key strokes.

|Operators | Description  |
|----|--------------------|
|=   |Assigns right operand value to the left operand.|
|+=  |Sums up left and right operand values and assigns the result to the left operand.|
|-=  |Subtract right operand value from the left operand value and assigns the result to the left operand.|
|*=  |Multiply left and right operand values and assigns the result to the left operand.|
|/=  |Divide left operand value by right operand value and assign the result to the left operand.|
|%=  |Get the modulus of left operand divide by right operand and assign resulted modulus to the left operand.|

**Ternary Operators:**

JavaScript provides a special operator called ternary operator `:?` that assigns a value to a variable based on some condition.

**Syntax:**

```js
<condition> ? <value1> : <value2>;

// Example
let a = 10, b = 20;

let c = a > b ? a : b; // 20
let d = a > b ? b : a; // 10
```

**typeof Operator:** It uses to find type of variable.

**Syntax:**

```js
typeof variable

// Example
Let a = 10;

typeof a // number
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 4.2. What are the bitwise operators available in javascript?

Below are the list of bit-wise logical operators used in JavaScript

|Operator	   |  Usage	      |   Description    |
|------------|---------|-----------------------|
|Bitwise AND |	a & b	 |Returns a one in each bit position for which the corresponding bits of both operands are ones.|
|Bitwise OR	 |a | b	   |Returns a one in each bit position for which the corresponding bits of either or both operands are ones.|
|Bitwise XOR |	a ^ b	 |Returns a one in each bit position for which the corresponding bits of either but not both operands are ones.|
|Bitwise NOT |	~ a	   |Inverts the bits of its operand.|
|Left shift	 |a << b	 |Shifts a in binary representation b (< 32) bits to the left, shifting in zeroes from the right.|
|Sign-propagating right shift|	a >> b |Shifts a in binary representation b (< 32) bits to the right, discarding bits shifted off.|
|Zero-fill right shift |	a >>> b	 | Shifts a in binary representation b (< 32) bits to the right, discarding bits shifted off, and shifting in zeroes from the left.|

**Examples:**

|Operation|	Result	  |Same as	    |Result    |
|---------|-----------|-------------|----------|
|5 & 1    | 1	        |0101 & 0001	|0001      |
|`5 | 1` 	| 5         |0101 | 0001  |0101      |
|`~ 5`    |-6	        |~0101	      |1010      |
|`5 << 1`	| 10        |0101 << 1  	|1010      |
|`5 ^ 1`	| 4         |0101 ^ 0001  |0100      |
|`5 >> 1`	| 2	        |0101 >> 1	  |0010      |
|5 >>> 1	| 2	        |0101 >>> 1	  |0010      |

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-bitwise-operators-nnz00d?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 4.3. What is the difference between == and === operators?

JavaScript provides both strict(===, !==) and type-converting(==, !=) equality comparison. The strict operators takes type of variable in consideration, while non-strict operators make type correction/conversion based upon values of variables. The strict operators follow the below conditions for different types,

1. Two strings are strictly equal when they have the same sequence of characters, same length, and same characters in corresponding positions.
2. Two numbers are strictly equal when they are numerically equal. i.e, Having the same number value.
   There are two special cases in this,
   1. NaN is not equal to anything, including NaN.
   2. Positive and negative zeros are equal to one another.
3. Two Boolean operands are strictly equal if both are true or both are false.
4. Two objects are strictly equal if they refer to the same Object.
5. Null and Undefined types are not equal with ===, but equal with ==. i.e,
    null===undefined --> false but null==undefined --> true

**Example:**

```js
0 == false // true
0 === false // false
1 == "1" // true
1 === "1" // false
null == undefined // true
null === undefined // false
"0" == false // true
"0" === false // false
[] === [] // false, refer different objects in memory
{} === {} // false, refer different objects in memory
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-comparison-0y16ii?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 4.4. What is typeof operator?

In JavaScript, the typeof operator returns the data type of its operand in the form of a string. The operand can be any object, function, or variable.

**Example:**

```js
typeof undeclaredVariable; // "undefined"

var a;
typeof a; // "undefined"

a = "Hello World";
typeof a; // "string"

a = 42;
typeof a; // "number"

a = 3.1415
typeof a; // "number"

a = true;
typeof a; // "boolean"

a = null;
typeof a; // "object"

a = undefined;
typeof a; // "undefined"

a = { b: "c" };
typeof a; // "object"

a = function () {
  return 10;
};

console.log(typeof a); // "function"
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-typeof-jesw53?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 4.5. What is an Unary operator?

The unary(+) operator is used to convert a variable to a number. If the variable cannot be converted, it will still become a number but with the value NaN.

**Example:**

```js
var x = "100";
var y = +x;
console.log(typeof x, typeof y); // string, number

var a = "Hello";
var b = +a;
console.log(typeof a, typeof b, b); // string, number, NaN
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-unary-operator-ld2luh?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 4.6. What is the purpose of delete operator?

The delete keyword is used to delete the property as well as its value.

```js
var user = {name: "Sadhika Chaudhuri", age: 24};
delete user.age;

console.log(user); // {name: "Sadhika Chaudhuri"}
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 4.7. What is a conditional operator in javascript?

The conditional (ternary) operator is the only JavaScript operator that takes three operands which acts as a shortcut for if statement.

```js
var isAuthenticated = false;

console.log(isAuthenticated ? 'Hello, welcome' : 'Sorry, you are not authenticated');
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 4.8. Can you apply chaining on conditional operator?

Yes, you can apply chaining on conditional operator similar to if … else if … else if … else chain.

**Example:**

```js
function getValue(someParam) {
  return condition1 ? value1
    : condition2 ? value2
    : condition3 ? value3
    : value4;
}

// The above conditional operator is equivalent to:
function getValue(someParam) {
  if (condition1) {
    return value1;
  } else if (condition2) {
    return value2;
  } else if (condition3) {
    return value3;
  } else {
    return value4;
  }
}
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 4.9. What is the difference between `==` and `===`?

The `==` is the abstract equality operator while `===` is the strict equality operator. The `==` operator will compare for equality after doing any necessary type conversions.

The `===` operator will not do type conversion, so if two values are not the same type `===` will simply return `false`. When using `==`, funky things can happen, such as:

```js
1 == '1'; // true
1 == [1]; // true
1 == true; // true
0 == ''; // true
0 == '0'; // true
0 == false; // true

let x = null;
console.log(x == null); // true
console.log(x == undefined); // true
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-equality-operator-lt2ngc?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 4.10. What is the difference between `typeof` and `instanceof` operator?

The `typeof` operator checks if a value has type of primitive type which can be one of boolean, function, object, number, string, undefined and symbol (ES6).

**Example:**

```js
const x = "Hello World";
const y = new String("Hello World");

typeof x; // returns 'string'
typeof y; // returns 'object'
```

The `instanceof` is a binary operator, accepting an object and a constructor. It returns a boolean indicating whether or not the object has the given constructor in its prototype chain.

```js
const a = "Hello World";
const b = new String("Hello World");

a instanceof String; // returns false
b instanceof String; // returns true
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-typeof-operator-9uejl1?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 4.11. What is the output of below spread operator array?

```js
[...'Hello']
```

**Output**:  ['H', 'e', 'l', 'l', 'o']  

**Explanation**: The string is an iterable type and the spread operator with in an array maps every character of an iterable to one element. Hence, each character of a string becomes an element within an Array.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>
