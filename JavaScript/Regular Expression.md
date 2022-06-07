## # 8. Regular Expression

<br/>

## Q 8.1. What is a RegExp object?

A regular expression is an object that describes a pattern of characters.

The JavaScript `RegExp` class represents regular expressions, and both String and `RegExp` define methods that use regular expressions to perform powerful pattern-matching and search-and-replace functions on text.

**Syntax:**

```js
// Using literal notation 
let pattern = /pattern/attributes;

// Using RegExp Object
let pattern = new RegExp(pattern, attributes);


// * pattern − A string that specifies the pattern of the regular expression or another regular expression.
// * attributes − An optional string containing any of the "g", "i", and "m" attributes that specify global, case-insensitive, and multi-line matches, respectively.
```

**Example:**

```js
let pattern = /ab+c/i; // literal notation

let pattern = new RegExp(/ab+c/, 'i') // constructor with regular expression literal as first argument
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 8.2. What are the string method available in regular expression?

Regular expressions are patterns used to match character combinations in strings. In JavaScript, regular expressions are also objects. These patterns are used with the `exec()` and `test()` methods of `RegExp`, and with the `match()`, `matchAll()`, `replace()`, `replaceAll()`, `search()`, and `split()` methods of String.

**Example 01:** `test()`

Tests for a match in a string. It returns `true` or `false`

```js
let exp = /Hello/;
let res1 = exp.test("Hello World");
let res2 = exp.test("Hi");

console.log(res1); // true
console.log(res2); // false
```

**Example 02:** `exec()`

Executes a search for a match in a string. It returns an array of information or `null` on a mismatch.

```js
let res1 = exp.exec("Hello World");
let res2 = exp.exec("Hi");

console.log(res1); // ['Hello', index: 0, input: 'Hello World', groups: undefined]
console.log(res2); // null
```

|Method	      |Description             |
|-------------|------------------------|
|exec()	      |Executes a search for a match in a string. It returns an array of information or `null` on a mismatch.|
|test()	      |Tests for a match in a string. It returns `true` or `false`.|
|match()	    |Returns an array containing all of the matches, including capturing groups, or `null` if no match is found.|
|matchAll()	  |Returns an iterator containing all of the matches, including capturing groups.|
|search()	    |Tests for a match in a string. It returns the index of the match, or `-1` if the search fails.|
|replace()	  |Executes a search for a match in a string, and replaces the matched substring with a replacement substring.|
|replaceAll()	|Executes a search for all matches in a string, and replaces the matched substrings with a replacement substring.|
|split()	    |Uses a regular expression or a fixed string to break a string into an array of substrings.|

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-regular-expression-fn79dp?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 8.3. What are modifiers in regular expression?

Modifiers can be used to perform case-insensitive and global searches.

| Modifier | Description |
|---- | -----------------|
| i  | Perform case-insensitive matching |
| g | Perform a global match rather than stops at first match  |
| m | Perform multiline matching|

**Example 01:** Global Search

```js
let text = "Hello World! Hello World!";
let pattern = /Hello/g;

console.log(text.match(pattern)); // ['Hello', 'Hello']
```

**Example 02:** Case-insensitive match

```js
let string = "Hello World!";
let pattern = /WORLD/i;

console.log(string.match(pattern2)); // ['World', index: 6, input: 'Hello World!', groups: undefined]
```

**Example 03:** Multiline match

The "m" modifier specifies a multiline match. It only affects the behavior of start `^` and end `$`. `^` specifies a match at the start of a string. `$` specifies a match at the end of a string.

```js
let paragraph = `Lorem Ipsum is simply dummy text of the printing and typesetting industry.`;

let pattern = /Lorem/m;

console.log(paragraph.match(pattern3)); // ["Lorem"]
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-modifier-sm7ul2)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 8.4. What are regular expression patterns?

Regular Expressions provided group of patterns in order to match characters. Basically they are categorized into 3 types,  

**Brackets:**

These are used to find a range of characters.

* **[...]**: Any one character between the brackets.
* **[^...]**: Any one character not between the brackets.
* **[0-9]**: It matches any decimal digit from **0** through **9**.
* **[a-z]**: It matches any character from lowercase **a** through lowercase **z**.
* **[A-Z]**: It matches any character from uppercase **A** through uppercase **Z**.
* **[a-Z]**: It matches any character from lowercase **a** through uppercase **Z**.

**Metacharacters:**

These are characters with a special meaning

* **.**: a single character
* **\s**: a whitespace character (space, tab, newline)
* **\S**: non-whitespace character
* **\d**: a digit (0-9)
* **\D**: a non-digit
* **\w**: a word character (a-z, A-Z, 0-9, _)
* **\W**: a non-word character
* **[\b]**: a literal backspace (special case).
* **[aeiou]**: matches a single character in the given set
* **[^aeiou]**: matches a single character outside the given set
* **(foo|bar|baz)**: matches any of the alternatives specified

**Quantifiers:**

These are useful to define quantities

* **p+**: It matches any string containing one or more p\'s.
* **p: It matches any string containing zero or more p\'s.
* **p?**: It matches any string containing at most one p.
* **p{N}**: It matches any string containing a sequence of **N** p\'s
* **p{2,3}**: It matches any string containing a sequence of two or three p\'s.
* **p{2, }**: It matches any string containing a sequence of at least two p\'s.
* **p$**: It matches any string with p at the end of it.
* **^p**: It matches any string with p at the beginning of it.

**Example:**

```js
// Brackets
"Hello World".match(/[a-d]/); // -> matches 'a'
"Hello World".match(/[A-D]/); // -> no match
"Hello World".match(/[A-D]/i); // -> matches 'a'

// Metacharacters
"Hello World".match(/[A-Za-z]\s[A-Za-z]/); // -> matches
"Hello World".match(/[0-9]\s[A-Za-z]/); // -> no match

// Quantifiers
"Hello".match(/l+/); // -> matches
"Hello".match(/A*/); // -> no match
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-regular-expression-patterns-b5ojtl?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 8.5. How do you search a string for a pattern?

**1. Using test()** It searches a string for a pattern, and returns `true` or `false`, depending on the result.

```js
let re1 = /Hi/;
let re2 = /you/;

re1.test("How are you?"); // false
re2.test("How are you?"); // true
```

**2. Using exec()** It searches a string for a specified pattern, and returns the found text as an object. If no match is found, it returns an empty (null) object.

```js
let re1 = /Hi/;
let re2 = /you/;

re1.exec("How are you?"); // null
re2.exec("How are you?"); // ["you"]
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-regular-expression-m10bgo?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 8.6. What is the purpose of exec method?

The purpose of exec method is similar to test method but it returns a founded text as an object instead of returning true/false.

```js
// Using test() method
var pattern = /you/;
console.log(pattern.test("How are you?")); // true


// Using exec() method
var pattern = /you/;
console.log(pattern.exec("How are you?")); // ["you", index: 8, input: "How are you?", groups: undefined]
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 8.7. How do you validate an email in javascript?

The `test()` method returns `true` if there is a match in the string with the regex pattern. The regular expression (regex) describes a sequence of characters used for defining a search pattern

```js
// Program to validate the email address

function validateEmail(email) {
  // regex pattern for email
  const re = /\S+@\S+\.\S+/g;

  // check if the email is valid
  let result = re.test(email);
  if (result) {
    console.log("Valid");
  } else {
    console.log("Not valid.");
  }
}

let email = "pradeep.kumar@gmail.com";
let email2 = "pradeep.kumar.com";

validateEmail(email); // Valid
validateEmail(email2); // Not Valid
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-regular-expression-rkxjb1?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 8.8. How do you detect a mobile browser using regexp?

You can detect mobile browser by simply running through a list of devices and checking if the useragent matches anything. This is an alternative solution for RegExp usage,

```js
function detectMobile() {
  if (
    navigator.userAgent.match(/Android/i) ||
    navigator.userAgent.match(/webOS/i) ||
    navigator.userAgent.match(/iPhone/i) ||
    navigator.userAgent.match(/iPad/i) ||
    navigator.userAgent.match(/iPod/i) ||
    navigator.userAgent.match(/BlackBerry/i) ||
    navigator.userAgent.match(/Windows Phone/i)
  ) {
    return true;
  } else {
    return false;
  }
}
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>
