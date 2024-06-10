# Crypto module in Node.js

The crypto module in Node.js is used to **provide users with cryptographic functionalities**. It provides a way of handling encrypted data.

This provides them with a large number of wrappers to perform various operations, including:

* Cipher
* Decipher
* Signing
* ashing

Let's see one example to understand it better...&#x20;

**Encrypt the text 'abc'**

{% code title="Encrypt the text 'abc'" %}
```javascript
var crypto = require('crypto');

var mykey = crypto.createCipher('aes-128-cbc', 'mypassword');
var mystr = mykey.update('abc', 'utf8', 'hex')
mystr += mykey.final('hex');

console.log(mystr); //34feb914c099df25794bf9ccb85bea72
```
{% endcode %}

{% code title="Decrypt back to 'abc'" %}
```javascript
var crypto = require('crypto');

var mykey = crypto.createDecipher('aes-128-cbc', 'mypassword');
var mystr = mykey.update('34feb914c099df25794bf9ccb85bea72', 'hex', 'utf8')
mystr += mykey.final('utf8');

console.log(mystr); //abc
```
{% endcode %}
