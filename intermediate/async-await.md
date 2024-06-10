# Async Await

* The `async` and `await` keywords enable asynchronous, promise-based behavior to be written in a cleaner style, avoiding the need to explicitly configure promise chains.
* The `await` keyword can only be used inside an `async` function.
* The `await` keyword makes the function pause the execution and wait for a resolved promise before it continues:

```javascript
function resolveAfter2Seconds() {
    return new Promise(resolve => {
        setTimeout(() => {
            resolve('resolved');
        }, 2000);
    });
}

async function asyncCall() {
    console.log('calling');  // calling
    const result = await resolveAfter2Seconds();
    console.log(result);    // resolved
}

asyncCall();
```

As shown below, the async code asks the JavaScript engine running the code to wait for the request.get() function to complete before moving on to the next line for execution.

<figure><img src="../.gitbook/assets/async await.png" alt=""><figcaption><p>async await</p></figcaption></figure>
