## # 10.EVENTS

<br/>

## Q 10.1. What is event handling in javascript?

The change in the state of an object is known as an **Event**. In html, there are various events which represents that some activity is performed by the user or by the browser.

When javascript code is included in HTML, js react over these events and allow the execution. This process of reacting over the events is called **Event Handling**. Thus, js handles the HTML events via **Event Handlers**.

Some of the HTML event handlers are:

**Mouse events:**

|Event Handler   |Description
|----------------|------------------------------|
|onclick         |When mouse click on an element|
|onmouseover     |When the cursor of the mouse comes over the element|
|onmouseout      |When the cursor of the mouse leaves an element|
|onmousedown     |When the mouse button is pressed over the element|
|onmouseup       |When the mouse button is released over the element|
|onmousemove     |When the mouse movement takes place.|

**Form events:**

|Event Handler |Description           |
|--------------|----------------------|
|onfocus       |When the user focuses on an element|
|onsubmit      |When the user submits the form|
|onblur        |When the focus is away from a form element|
|onchange      |When the user modifies or changes the value of a form element|

**Window/Document events:**

|Event Handler  |Description            |
|---------------|-----------------------|
|onload         |When the browser finishes the loading of the page|
|onunload       |When the visitor leaves the current webpage, the browser unloads it|
|onresize       |When the visitor resizes the window of the browser|

**Example:** Click Event

```html
<!DOCTYPE html>
<html>
  <head>
    <script>
      function greeting() {
        alert("Hello! Good morning");
      }
    </script>
  </head>
  <body>
    <h2>Click Event Example</h2>
    <button type="button" onclick="greeting()">Click me</button>
  </body>
</html>
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-click-event-rcvg65?file=/index.html)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 10.2. How to create and trigger events in javascript?

Events can be handled either through `addEventListener()` method or we can trigger events on individual components by defining specific JavaScript functions.

**Syntax:**

```js
document.addEventListener(event, function, phase)
```

**Example:**

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Click Event</title>
    <meta charset="UTF-8" />
  </head>
  <body>
    <h3>Click on the page to trigger click event</h3>
    <script type="text/javascript">
      document.addEventListener("click", function () {
        console.log("You clicked inside the document");
      });
    </script>
  </body>
</html>
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-addeventlistener-kxesqw?file=/index.html)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 10.3. What is an event delegation?

Event Delegation is basically a pattern to handle events efficiently. Instead of adding an event listener to each and every similar element, we can add an event listener to a parent element and call an event on a particular target using the `event.target` property of the event object.

**Example:**

```html
<div id="buttons"> 
  <button class="buttonClass">Click me</button>
  <button class="buttonClass">Click me</button>
  <button class="buttonClass">Click me</button>
</div>

<script>
  document.getElementById('buttons')
    .addEventListener('click', event => { 
      if (event.target.className === 'buttonClass') { 
        console.log('Click!');
      }
    });
</script>
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-event-delegation-7x5idt?file=/index.html)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 10.4. What is an event flow?

Event flow is the order in which event is received on the web page. When you click an element that is nested in various other elements, before your click actually reaches its destination, or target element, it must trigger the click event each of its parent elements first, starting at the top with the global window object.

There are two ways of event flow

* Top to Bottom (Event Capturing)
* Bottom to Top (Event Bubbling)

<p align="center">
  <img src="assets/event-flow.png" alt="Event Flow" width="500px" />
</p>

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 10.5. What is event bubbling?

Event bubbling is a type of event propagation where the event first triggers on the innermost target element, and then successively triggers on the ancestors (parents) of the target element in the same nesting hierarchy till it reaches the outermost DOM element.

**Example**: If you click on EM, the handler on DIV runs.  

```html
<div onclick="alert('The handler!')">
  <em>If you click on <code>EM</code>, the handler on <code>DIV</code> runs.</em>
</div>
```

**Stopping bubbling:**  

```html
<body onclick="alert(`the bubbling doesn\'t reach here`)">
  <button onclick="event.stopPropagation()">Click me</button>
</body>
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-event-bubbling-y1sjrk?file=/index.html)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 10.6. What is event capturing?

Event capturing is a type of event propagation where the event is first captured by the outermost element and then successively triggers on the descendants (children) of the target element in the same nesting hierarchy till it reaches the inner DOM element.

**Example:**

```html
<article id="ancestor">
    Article Element
    <div id="parent">
      DIV Element
      <p id="child">
        P Element
      </p>
    </div>
</article>

<script>
  // Script to click event handler to capture on each element
  for (let elem of document.querySelectorAll("*")) {
    elem.addEventListener(
      "click",
      (e) => console.log("Capturing:", elem.tagName),
      true
    );
  }
</script>
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-event-capturing-mz6d16?file=/index.html)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 10.7. How do you submit a form using JavaScript?

Generally, a form is submitted when the user presses a submit button. JavaScript provides the form object that contains the `submit()` method. Use the "id" of the form to get the form object.

**Example:**

```html
<form id="myForm" action="/action_page.php">
  Search: <input type='text' name='query' />
  <input type="button" onclick="handleSubmit()" value="Submit form">
</form>

<script>
function handleSubmit() {
  document.getElementById("myForm").submit();
}
</script>
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 10.8. What is the purpose of void(0)?

The `void(0)` is used to prevent the page from refreshing. This will be helpful to eliminate the unwanted side-effect, because it will return the `undefined` primitive value.

It is commonly used for HTML document that uses `href="JavaScript:void(0);"` within an `<a>` element. i.e, when you click a link, the browser loads a new page or refreshes the same page. But this behavior will be prevented using this expression.  

**Example:** the below link notify the message without reloading the page

```html
<a href="JavaScript:void(0);" onclick="alert('Prevent the page from refreshing!')">Click Me!</a>
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-void-onx4n5?file=/index.html)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 10.9. What is the use of preventDefault method?

The `preventDefault()` method is used to prevent the browser from executing the default action of the selected element. It can prevent the user from processing the request by clicking the link.

For example, prevent form submission when clicking on submit button and prevent opening the page URL when clicking on hyper link are some common usecases.

```js
document.getElementById("link").addEventListener("click", function(event) {
   event.preventDefault();
});
```

*Note: Remember that not all events are cancelable*.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 10.10. What is the use of stopPropagation method?

The `stopPropagation` method is used to stop the event from bubbling up the event chain.

For example, the below nested divs with stopPropagation method prevents default event propagation when clicking on nested div(Div1)

```html
<p>Click DIV1 Element</p>
<div onclick="secondFunc()">DIV 2
  <div onclick="firstFunc(event)">DIV 1</div>
</div>

<script>
function firstFunc(event) {
  alert("DIV 1");
  event.stopPropagation();
}

function secondFunc() {
  alert("DIV 2");
}
</script>
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 10.11. What is difference between stoppropagation, stopimmediatepropagation and preventdefault in javascript?

**1. event.preventDefault()**:

This method is used to stop the browser\'s default behavior when performing an action.

**Example:**

```html
<p>Please click on the checkbox control.</p>

<form>
  <label for="id-checkbox">Checkbox:</label>
  <input type="checkbox" id="id-checkbox" />
</form>

<div id="output-box"></div>

<script>
  document.querySelector("#id-checkbox").addEventListener("click", function(event) {
  document.getElementById("output-box").innerHTML += "Sorry! <code>preventDefault()</code> won't let you check this!<br>";
  event.preventDefault();
}, false);
</script>
```

**2. event.stopPropagation()**:

This method is used to prevent the propagation of an event as defined in the capturing/bubbling phase of the flow of an event in the browser.

**Example:**

```html
<div class="parent" (onClick)="console.log('parent')">
    <button class="child" (onClick)="buttonClick(event)"></button>
</div>
<script>
    function buttonClick(event) {
        event.stopPropagation();
        console.log('child');
    }
</script>
```

**3. event.stopImmediatePropagation()**:

With `stopImmediatePropagation()`, along with the event propagation, other event handlers will also be prevented from execution.

As a result, clicking on the div element will:

* Prevent event bubbling to the parent elements
* Prevent the execution of any other event listener attached to the element

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 10.12. What is the use of setTimeout?

The `setTimeout()` method is used to call a function or evaluates an expression after a specified number of milliseconds.

**Syntax:**

```js
setTimeout(callback function, delay in milliseconds)
```

**Example:**

```js
setTimeout(() => {
  console.log("Delayed for 1 second.");
}, "1000")
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 10.13. What is the use of setInterval?

The `setInterval()` method is used to call a function or evaluates an expression at specified intervals (in milliseconds). The `setInterval()` method continues calling the function until `clearInterval()` is called, or the window is closed.

**Example:**

```html
<p id="timer"></p>

<script>
setInterval(myTimer, 1000);

function myTimer() {
  const date = new Date();
  document.getElementById("timer").innerHTML = date.toLocaleTimeString();
}
</script>
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-setinterval-6tx5pq?file=/index.html)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 10.14. What is the purpose of clearTimeout method?

The `clearTimeout()` function is used in javascript to clear the timeout which has been set by `setTimeout()` function before that. i.e, The return value of setTimeout() function is stored in a variable and it\'s passed into the `clearTimeout()` function to clear the timer.

For example, the below setTimeout method is used to display the message after 3 seconds. This timeout can be cleared by clearTimeout() method.

```js
// clearTimeout()

var msg;
function greeting() {
  console.log("Hello World!");
  stop();
}
function start() {
  console.log("start");
  msg = setTimeout(greeting, 3000);
}
function stop() {
  console.log("stop");
  clearTimeout(msg);
}

start();

// Output
Start
Hello World!
Stop
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-cleartimeout-w6ve8y?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 10.15. What is the purpose of clearInterval method?

The `clearInterval()` function is used in javascript to clear the interval which has been set by `setInterval()` function. i.e, The return value returned by setInterval() function is stored in a variable and it\'s passed into the clearInterval() function to clear the interval.

For example, the below setInterval method is used to display the message for every 3 seconds. This interval can be cleared by clearInterval() method.

```js
// clearInterval()

var msg;
function greeting() {
  console.log("Hello World!");
  stop();
}
function start() {
  console.log("start");
  msg = setInterval(greeting, 3000);
}
function stop() {
  console.log("stop");
  clearInterval(msg);
}

start();

// Output
Start
Hello World!
Stop
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-clearinterval-brugdh?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q 10.16. What is the difference between document load and DOMContentLoaded events?

The `DOMContentLoaded` event is fired when the initial HTML document has been completely loaded and parsed, without waiting for assets(stylesheets, images, and subframes) to finish loading. Whereas The load event is fired when the whole page has loaded, including all dependent resources(stylesheets, images).

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>
