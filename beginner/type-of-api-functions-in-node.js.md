# Type of API functions in Node.js

1. **Asynchronous**, non-blocking functions
2. **Synchronous**, blocking functions

### **Asynchronous vs Non-blocking**

* **Asynchronous**
  * Using these, we can make **asynchronous HTTP requests** that **do not wait for the server to respond**.
    * These functions **continue to respond** to the request for which it has already received the server response.
* **Non-blocking**
  * Non-blocking functions are used in regard to **I/0 operations**.
  * They **immediately respond with whatever data is available** and keep on running as per the requests.
