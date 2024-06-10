# Node.js timing features

The Timers module in _Node_._js_ contains _functions_ that execute code after a set period of time. It includes the [**setTimeout()**](node.js-timing-features.md#settimeout)**,** [**setImmediate()**](node.js-timing-features.md#setimmediate)**,** and [**setInterval()**](node.js-timing-features.md#setinterval) methods.

## **setTimeout()**

The setTimeout() method is used to execute code after a specified number of milliseconds. The specified function will be **executed once**. We can use the **clearTimeout() method to prevent the function from running**. The setTimeout() method returns an ID that can be used in the clearTimeout() method.

**Syntax:**

```
setTimeout(callback, delay, args)
```

**Parameters:**

* **callback:** This parameter holds the function that to be executed.
* **delay:** This parameter holds the number of milliseconds to wait before calling the callback function.
* **args:** This parameter holds the optional parameter.

**Example:**

```javascript
let name = 'Nandeep';

setTimeout(function () {
	return console.log(name);
}, 5000);

// This console log is executed right away
console.log('Executing setTimeout() method');
```

**Output:**

```bash
Executing setTimeout() method
Nandeep
```

Notice that the console is executing first. The trick to realizing this is that the code is only guaranteed to execute after at least that length of time has passed.



## **setImmediate()**

The setImmediate() method is used to **execute code at the end of the current event loop cycle**. Any function passed as the setImmediate() argument is a callback that can be executed in the next iteration of the event loop.

**Syntax:**

```
setImmediate(callback, args)
```

**Parameters:**

* **callback:** This parameter holds the function to call at the end of this turn of the Node.js Event Loop.
* **args:** This parameter holds the optional arguments for the function.

**Example:**

```javascript
setTimeout(function () {
	console.log('setTimeout() function running');
}, 5000);

// An interval
setInterval(function () {
	console.log('setInterval() function running');
}, 5000);

// An immediate, its callback will be
// executed before those defined above
setImmediate(function () {
	console.log('setImmediate() function running');
});

// IO callbacks and code in the normal
// event loop runs before the timers
console.log('Simple statement in the event loop');
```

**Output:**

```bash
Simple statement in the event loop
setImmediate() function running
setTimeout() function running
setInterval() function running
setInterval() function running
setInterval() function running
setInterval() function running
. . .
```

Notice, how even though setImmediate function is defined after setTimeout and setInterval functions, it runs ahead of them.

The **`clearImmediate` function** is used to clear the function call scheduled by the `setImmediate` function. Both these functions are found in the `Timers` module of Node.js.

```javascript
clearImmediate(timerIdentifier);
```

```javascript
console.log("Before the setImmediate call")
let timerID = setImmediate(() => {console.log("Hello, World")});
console.log("After the setImmediate call")
clearImmediate(timerID);
```

## **setInterval()**

The setInterval() method is **used to call a function at specified intervals (in milliseconds)**. It is used to execute the function only once after a specified period.\
We can use the **clearInterval()** method to prevent the function from running. The setInterval() method returns the ID which can be used in clearInterval() method.

**Syntax:**

```javascript
setInterval(callback, delay, args)
```

**Parameters:**

* **callback:** This parameter holds the function that is to be called when the timer elapses.
* **delay:** This parameter holds the number of milliseconds to wait before calling the callback function.
* **args:** This parameter holds the optional arguments for the function.

**Example:**

```javascript
setInterval(function () {
    console.log('Hello Friends');
}, 5000);
```

**Output:**

```bash
Hello Friends
Hello Friends
.....
```

It will print output **multiple times with a time interval of 5 seconds**.
