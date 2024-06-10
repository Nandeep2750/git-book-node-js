# Single-Threaded Concurrency in Node.js

## Why is Node.js single-threaded?

* Node.js uses a single-threaded model to **support async processing**.
* With async processing, an application can perform better and be more scalable under web loads.
* Node.js uses a single-threaded model approach rather than a typical thread-based implementation.

{% hint style="info" %}
Node.js **supports async processing,** so we can perform multiple operations at the same time.
{% endhint %}

## If Node.js is single-threaded, then how does it handle concurrency?

Node.js handles concurrency using a single-threaded event loop model rather than a multi-threaded request/response model. It leverages JavaScript's event-driven architecture and callback system to efficiently manage numerous concurrent client requests. The event loop is central to this approach, allowing Node.js to perform non-blocking I/O operations and handle multiple connections simultaneously. **The event loop is the processing model's beating heart in Node.js.**
