# Purpose of NODE\_ENV

NODE\_ENV is an environment variable in the express server that stands for node environment. The NODE\_ENV environment variable specifies the environment in which an application is running (usually, development or production).

Depending on this an application may perform specific tasks like turn debugging on or off, listen on a specific port, etc.

\
**NODE\_ENV as a performance booster:** One of the simplest things we can do to improve performance is to set NODE\_ENV to "production."&#x20;

Setting NODE\_ENV to “production” makes Express:

* Cache view templates.
* Cache CSS files generated from CSS extensions.
* Generate less verbose error messages.

Thereby improving the performance of the application which is comparatively slower in development.



### **How to properly set NODE\_ENV?**

NODE\_ENV works like any other environment variable. How to set it depends on the platform being used.

<pre><code><strong>On Linux and OSX: export NODE_ENV=production
</strong><strong>On Windows: $env:NODE_ENV = 'production'
</strong></code></pre>

**Set at the time of starting the application:** On all platforms, we can explicitly set the NODE\_ENV at the time of starting the application, like:&#x20;

```
NODE_ENV=production node app.js
```

**Accessing NODE\_ENV:** We can access NODE\_ENV like any other environment variable using the _process_ and _env_ of NodeJS, as we have already seen while learning about environment variables.

```
process.env.NODE_ENV
```

**We can write environment-specific code by checking the value of NODE\_ENV by using `process.env.NODE_ENV`**

```javascript
var environment = process.env.NODE_ENV;

switch (environment) {
    case 'development':
        /* connect to local database
        Do something specific
        to development environment. */
        break;
    case 'production':
        /* Do something specific
        to production environment. */
        break;
    default:
        break;
}
```
