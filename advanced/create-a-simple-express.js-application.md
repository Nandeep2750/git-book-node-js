# Create a simple Express.js application

* The request object represents the HTTP request and has properties for the request query string, parameters, body, HTTP headers, and so on
* The response object represents the HTTP response that an Express app sends when it receives an HTTP request

Steps to follow...

**Step 1:** initialize the package file

```
npm init
```

This will ask you for a few configurations about your project; you can fill them out accordingly, or you can change them later from the **package.json** file.&#x20;

<figure><img src="../.gitbook/assets/npm init" alt=""><figcaption><p>initialize package file for new project</p></figcaption></figure>

**Step 2:** Install the necessary dependencies for our application

```
npm install express
```

Something like this will be shown on successful installation,

<figure><img src="../.gitbook/assets/install express package" alt=""><figcaption><p>install express package</p></figcaption></figure>

**Step 3:** The project structure will look like the following:

<figure><img src="../.gitbook/assets/express js project structure" alt=""><figcaption><p>express js project structure</p></figcaption></figure>

Create a file **app.js,** for this article, we will write the whole express code in that file.

* Create a file **app.js,** for this article, we will write the whole express code in that file.
* This will be our folder structure. Now Inside app.js, Import express with require keyword and create an app by calling the **express()** function provided by the express framework.&#x20;
* Set the port for our local application, 3000 is the default but you can choose any according to the availability of ports. Call the **listen()** function, It requires a path and callback as an argument.&#x20;
* It starts listening to the connection on the specified path, the default host is localhost, and our default path for the local machine is **localhost:3000**, here 3000 is the port that we set earlier. The **callback function gets executed either on the successful start of the server or due to an error.**

```javascript
const express = require('express');

const app = express();
const PORT = 3000;

app.listen(PORT, (error) => {
    if (!error)
        console.log("Server is Successfully Running, and App is listening on port " + PORT)
    else
        console.log("Error occurred, server can't start", error);
});
```

**Step to run the application:** Now as we have created a server we can successfully start running it to see if it’s working, write this command in your terminal to start the express server.&#x20;

```
node app.js
```

**Output:** You will see something like this on the terminal.

<figure><img src="../.gitbook/assets/Express.js Server started" alt=""><figcaption></figcaption></figure>
