---
description: How to avoid callback hell in Node.js
---

# Prevent callback hell

**We can avoid callback hell with the help of Promises**. Promises in Javascript are a way to handle asynchronous operations in Node.js. It allows us to return a value from an asynchronous function like a synchronous function. When we return something from an asynchronous method it returns a promise which can be used to consume the final value when it is available in the future with the help of `then()` method or `await` inside of async functions. The syntax to create a promise is mentioned below.

```javascript
const promise = new Promise(function(resolve, reject){
     // code logic
});
```

**Example:** In the code example mentioned below, we simulate an asynchronous add operation with the help of setTimeout().&#x20;

* First, we create an add() function that takes three arguments of which two are the numbers that we want to add and the third one is the callback function which is called with the result of adding operations after 2 seconds. Then, we calculate the result of the addition of the first four natural numbers using a nested callback to simulate a callback hell.
* After that, we **create an addPromise()** function that returns a promise and this promise is resolved after two seconds of calling the function. Then we consume the promise using the then() method and async/await.

{% code title="Without Promise" %}
```javascript
// The callback function for the function
// is executed after two seconds with
// the result of the addition
const add = function (a, b, callback) {
    setTimeout(() => {
        callback(a + b);
    }, 2000);
};

// Using nested callbacks to calculate
// the sum of first four natural numbers.
add(1, 2, (sum1) => {
    add(3, sum1, (sum2) => {
        add(4, sum2, (sum3) => {
            console.log(`Sum of the first 4 natural numbers using callback is ${sum3}`);  // Sum of the first 4 natural numbers using callback is 10
        });
    });
});

```
{% endcode %}

```javascript
/* Use of Promise with then() for prevent callback hell */

// This function returns a promise
// that will later be consumed to get
// the result of the addition
const addPromise = function (a, b) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(a + b);
        }, 2000);
    });
};

// Consuming promises with the chaining of then()
// method and calculating the result
addPromise(1, 2)
    .then((sum1) => { return addPromise(3, sum1); })
    .then((sum2) => { return addPromise(4, sum2); })
    .then((sum3) => { console.log(`Sum of first 4 natural numbers using promise and then() is ${sum3}`); });
```

```javascript
/* Use of Promise with async await to prevent callback hell */

const addPromise = function (a, b) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(a + b);
        }, 2000);
    });
};

// Calculation the result of addition by
// consuming the promise using async/await
(async () => {
    const sum1 = await addPromise(1, 2);
    const sum2 = await addPromise(3, sum1);
    const sum3 = await addPromise(4, sum2);

    console.log(`Sum of first 4 natural numbers using promise and async/await is ${sum3}`);
})();
```
