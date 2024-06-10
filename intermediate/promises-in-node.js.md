# Promises in Node.js

Promises in Node.js are objects representing the eventual completion (or failure) of an asynchronous operation and its resulting value. They provide a more structured and cleaner way to handle asynchronous operations compared to callbacks, helping to avoid issues such as "callback hell."

Promises in Javascript are a way to handle asynchronous operations in Node.js. It allows us to return a value from an asynchronous function like a synchronous function. When we return something from an asynchronous method it returns a promise which can be used to consume the final value when it is available in the future with the help of `then()` method or `await` inside of async functions. The syntax to create a promise is mentioned below.

```javascript
const promise = new Promise(function(resolve, reject){
     // code logic
});
```

## **Basic Concept**

A Promise can be in one of three states:

* **Pending**: Initial state, neither fulfilled nor rejected.
* **Fulfilled**: Operation completed successfully.
* **Rejected**: Operation failed.

## **Creating and Using Promises**

Here's a simple example to illustrate how Promises work in Node.js:

```javascript
// Creating a new Promise
const myPromise = new Promise((resolve, reject) => {
    // Simulate an asynchronous operation using setTimeout
    setTimeout(() => {
        const success = true; // Change to false to simulate a failure
        if (success) {
            resolve('Operation succeeded!');
        } else {
            reject('Operation failed!');
        }
    }, 1000);
});

// Using the Promise
myPromise
    .then((message) => {
        console.log(message); // This will run if the Promise is resolved
    })
    .catch((error) => {
        console.error(error); // This will run if the Promise is rejected
    });

console.log('This will run before the Promise is settled');
```

### **Explanation**

1. **Creating a Promise**:
   * A new `Promise` is created with a function that takes two arguments: `resolve` and `reject`.
   * Inside this function, we simulate an asynchronous operation using `setTimeout`.
   * Depending on the outcome, we call `resolve` with a success message or `reject` with an error message.
2. **Using the Promise**:
   * The `then` method is used to handle the resolved value of the Promise.
   * The `catch` method is used to handle any errors (rejections).
3. **Non-blocking behaviour**:
   * The message `console.log('This will run before the Promise is settled');` demonstrates that the Promise runs asynchronously. This message is logged before the Promise is settled.

## Prevent Callback Hell

First of all, let's consider an example that we've seen in callback hell. Here is the solution to that callback hell using promises.

```javascript
const readFile = (filename) => {
    return new Promise((resolve, reject) => {
        fs.readFile(filename, 'utf8', (err, data) => {
            if (err) {
                reject(err);
            } else {
                resolve(data);
            }
        });
    });
};

readFile('file1.txt')
    .then((data1) => readFile('file2.txt'))
    .then((data2) => readFile('file3.txt'))
    .then((data3) => {
        // Handle data from file3
    })
    .catch((err) => {
        console.error('Error:', err);
    });

```

**Example:** In the code example mentioned below, we simulate an asynchronous add operation with the help of setTimeout().&#x20;

* First, we create an add() function that takes three arguments of which two are the numbers that we want to add and the third one is the callback function which is called with the result of adding operations after 2 seconds. Then, we calculate the result of the addition of the first four natural numbers using a nested callback to simulate a callback hell.
* After that, we **create an addPromise()** function that returns a promise and this promise is resolved after two seconds of calling the function. Then we consume the promise using the then() method and async/await.

{% code title="Without Promise" %}
```javascript
// The callback function for the function is executed after two seconds with the result of the addition
const add = function (a, b, callback) {
    setTimeout(() => {
        callback(a + b);
    }, 2000);
};

// Using nested callbacks to calculate the sum of the first four natural numbers.
add(1, 2, (sum1) => {
    add(3, sum1, (sum2) => {
        add(4, sum2, (sum3) => {
            console.log(`Sum of the first 4 natural numbers using a callback is ${sum3}`);  // Sum of the first 4 natural numbers using callback is 10
        });
    });
});

```
{% endcode %}

{% code title="With Promise [then() method]" %}
```javascript
/* Use of Promise with then() for prevent callback hell */

// This function returns a promise that will later be consumed to get the result of the addition
const addPromise = function (a, b) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(a + b);
        }, 2000);
    });
};

// Consuming promises with the chaining of then() method and calculating the result
addPromise(1, 2)
    .then((sum1) => { return addPromise(3, sum1); })
    .then((sum2) => { return addPromise(4, sum2); })
    .then((sum3) => { console.log(`Sum of first 4 natural numbers using promise and then() is ${sum3}`); });
```
{% endcode %}

{% code title="With Promise [async/await]" %}
```javascript
/* Use of Promise with async await to prevent callback hell */

const addPromise = function (a, b) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(a + b);
        }, 2000);
    });
};

// Calculation of the result of addition by consuming the promise using async/await
(async () => {
    const sum1 = await addPromise(1, 2);
    const sum2 = await addPromise(3, sum1);
    const sum3 = await addPromise(4, sum2);

    console.log(`Sum of first 4 natural numbers using promise and async/await is ${sum3}`);
})();
```
{% endcode %}

## **Chaining Promises**

Promises can be chained to perform multiple asynchronous operations in sequence:

```javascript
firstPromise = new Promise((resolve, reject) => {
    setTimeout(() => resolve('First operation completed'), 1000);
});

firstPromise
    .then((message) => {
        console.log(message);
        return new Promise((resolve, reject) => {
            setTimeout(() => resolve('Second operation completed'), 1000);
        });
    })
    .then((message) => {
        console.log(message);
    })
    .catch((error) => {
        console.error(error);
    });
```

In this example, the second Promise is returned from the first `then` method, allowing the operations to be performed sequentially.

## Advantages of Using Promises Instead of Callbacks

1. **Avoid Callback Hell**: Promises enable chaining of operations, facilitating a more readable and maintainable code structure. This avoids the problem of deeply nested callback functions, known as "callback hell."
2. **Improved Readability**: Promises provide a more linear and cleaner way to handle asynchronous operations compared to nested callbacks. This leads to code that is easier to understand and maintain.
3. **Specific and Structured Control Flow**: Promises offer a more structured control flow for asynchronous logic. With methods like `.then()` and `.catch()`, developers can specify the sequence of operations and error handling, enhancing code organization and clarity.
4. **Low Coupling**: Promises promote loose coupling between asynchronous tasks and their handlers. Each Promise represents a single asynchronous task, allowing for better separation of concerns and modularization of code.
5. **Built-in Error Handling**: Promises come with built-in error handling mechanisms, such as the `.catch()` method. Errors thrown within a Promise chain can be easily caught and handled at a centralized location, improving code maintainability and debugging.
6. **Standardization**: Promises follow a standardized interface, making it easier for developers to understand and work with asynchronous code across different libraries and frameworks. This fosters consistency and interoperability within the Node.js ecosystem and beyond.

In summary, Promises in Node.js provide a robust way to handle asynchronous operations, offering improved readability, better error handling, and a more structured control flow compared to traditional callback-based asynchronous programming. This leads to more maintainable and scalable codebases.
