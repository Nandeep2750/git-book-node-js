# Event Driven Programming

An event-driven programming approach uses events to trigger various functions. An event can be anything, such as typing a key or clicking a mouse button. A call-back function is already registered with the element and executes whenever an event is triggered.



It means that as soon as **Node starts its server, it simply initiates its variables, declares functions, and then simply waits for events to occur.** It is one of the reasons why Node.js is pretty fast compared to other similar technologies.

There is a main loop in the event-driven application that listens for events and then triggers a callback function when one of those events is detected.

<figure><img src="../.gitbook/assets/Event Driven Programming" alt=""><figcaption></figcaption></figure>

### **What is an event loop?**

An **event loop** in Node.js handles all the asynchronous callbacks in an application.

This approach mainly follows the **publish-subscribe pattern**.\
