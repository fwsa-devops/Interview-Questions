## # 5. NUMBERS

<br/>

## Q 5.1. How do you generate random integers?

The `Math.random()` function returns a floating-point, pseudo-random number in the range 0 to less than 1 (inclusive of 0, but not 1). For example, if you want generate random integers between 1 to 100, the multiplication factor should be 100,

```js
// Example 01:
Math.random(); // returns a random integer between 0 to 1

// Example 02:
Math.floor(Math.random() * 100) + 1; // returns a random integer from 1 to 100

// Example 03:
function getRandomNumber(max) {
  return Math.floor(Math.random() * max) + 1;
}

console.log(getRandomNumber(10)); // returns a random integer from 1 to 10
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-random-number-slllvd?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 5.2. What is isNaN?

The `isNaN()` function determines whether a value is NaN ( Not a Number ) or not. This function returns `true` if the value equates to NaN. The `isNaN()` method converts the value to a number before testing it.

```js
isNaN('Hello') // true

isNaN('100') // false

typeof NaN // Number

Number.isNaN('Hello'); // false
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-isnan-6w1huz?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 5.3. What is the purpose of isFinite function?

The global `isFinite()` function determines whether the passed value is a finite number. It returns `false` if the value is `+infinity`, `-infinity`, or `NaN` (Not-a-Number), otherwise it returns true.

```js
isFinite(Infinity);  // false
isFinite(NaN);       // false
isFinite(-Infinity); // false

isFinite(100);  // true
isFinite(1/0); // false

Number.isFinite(0 / 0); // false
Number.isFinite(null); // false
Number.isFinite("123") // false
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-isfinite-5sl988?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 5.4. Explain NEGATIVE_INFINITY in JavaScript?

The `Number.NEGATIVE_INFINITY` property represents the negative Infinity value.

**Syntax:**

```js
Number.NEGATIVE_INFINITY
```

* Negative infinity is a number in javascript, which is derived by 'dividing negative number by zero'.
* A number object needs not to be created to access this static property.
* The value of negative infinity is the same as the negative value of the infinity property of the global object.

```js
// NEGATIVE_INFINITY
console.log(Number.NEGATIVE_INFINITY); // -Infinity
console.log(Number.MAX_VALUE + Number.MAX_VALUE); // Infinity
console.log(-2 * Number.MAX_VALUE); // -Infinity

console.log("Math.pow(10, 1000): " + Math.pow(10, 1000)); // Infinity 
console.log("Math.log(0): " + Math.log(0)); // -Infinity

console.log(Number.NEGATIVE_INFINITY === -2 * Number.MAX_VALUE); // true
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-negative-infinity-1gmh0r?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>
