# How does Node.js work?

* Node.js is a **virtual machine** that uses JavaScript as its scripting language and runs on a v8 environment.&#x20;
* **It works on a single-threaded event loop** and a **non-blocking I/0** which provides a high rate as it can handle a higher number of concurrent requests.&#x20;
* By making use of the 'HTTP' module, Node.js can **run on any stand-alone web server**.

A web server using Node.js typically has a workflow that is quite similar to the diagram illustrated below. Let’s explore this flow of operations in detail.

<figure><img src="https://www.simplilearn.com/ice9/free_resources_article_thumb/Node.js_Architecture_Workflow.png" alt="Node.js Architecture Workflow" width="563"><figcaption><p>Node.js Architecture Workflow</p></figcaption></figure>

* Clients send requests to the webserver to interact with the web application. Requests can be non-blocking or blocking:
* Querying for data
* Deleting data&#x20;
* Updating the data
* Node.js retrieves the incoming requests and adds those to the Event Queue
* The requests are then passed one by one through the Event Loop. It checks if the requests are simple enough not to require any external resources
* The Event Loop processes simple requests (non-blocking operations), such as I/O Polling, and returns the responses to the corresponding clients

A single thread from the Thread Pool is assigned to a single complex request. This thread is responsible for completing a particular blocking request by accessing external resources, such as computation, database, file system, etc.

Once the task is carried out completely, the response is sent to the Event Loop which sends that response back to the client.
