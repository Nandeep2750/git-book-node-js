# File System (FS)

In Node.js, file I/O is provided by simple wrappers around standard POSIX functions. Node File System (fs) module can be imported using the following syntax:

**Syntax:**

```javascript
var fs = require("fs")
```

## Node.js FS Reading File

Every method in the fs module has synchronous and asynchronous forms.

Asynchronous methods take the last parameter as a completion function callback. The asynchronous method is preferred over the synchronous method because it never blocks the program execution, whereas the synchronous method blocks.

Create a text file named "input.txt" having the following content.

{% code title="" overflow="wrap" %}
```
Javatpoint is one of the best online tutorial website to learn different technologies in a very easy and efficient manner.  
```
{% endcode %}

Let's take an example to create a JavaScript file named "main.js" having the following code:

```javascript
var fs = require("fs");

// ---- Asynchronous read ----
fs.readFile('input.txt', function (err, data) {
    if (err) {
        return console.error(err);
    }
    console.log("Asynchronous read: " + data.toString());
});


// ---- Synchronous read ----
var data = fs.readFileSync('input.txt');
console.log("Synchronous read: " + data.toString());
console.log("Program Ended");  
```

Open the Node.js command prompt and run the main.js:

```bash
node main.js
```

## Node.js Open a file

**Syntax:** The following is the syntax of the method to open a file in asynchronous mode:

```javascript
fs.open(path, flags[, mode], callback)
```

**Parameter explanation:** Following is the description of parameters used in the above syntax:

* **path:** This is a string having a file name including a path.
* **flags:** Flag specifies the behavior of the file to be opened. All possible values have been mentioned below.
* **mode:** This sets the file mode (permission and sticky bits), but only if the file was created. It defaults to 0666, readable and writeable.
* **callback:** This is the callback function that gets two arguments (err, fd).

### What are some of the flags used in the read/write operations in files?

Following is a list of flags for read/write operations:

<table><thead><tr><th width="100">Flag</th><th>Description</th></tr></thead><tbody><tr><td>r</td><td>open file for <strong>reading</strong>. an exception occurs if the file does not exist.</td></tr><tr><td>r+</td><td>open file for <strong>reading and writing</strong>. an exception occurs if the file does not exist.</td></tr><tr><td>rs</td><td>open file for <strong>reading in synchronous mode</strong>.</td></tr><tr><td>rs+</td><td>open file for <strong>reading and writing</strong>, telling the os to open it synchronously. see notes for 'rs' about using this with caution.</td></tr><tr><td>w</td><td>open file for <strong>writing</strong>. the file is created (if it does not exist) or truncated (if it exists).</td></tr><tr><td>wx</td><td>like 'w' but fails if path exists.</td></tr><tr><td>w+</td><td>open file for <strong>reading and writing</strong>. the <strong>file is created (if it does not exist)</strong> or <strong>truncated (if it exists)</strong>.</td></tr><tr><td>wx+</td><td>like 'w+' but <strong>fails if path exists</strong>.</td></tr><tr><td>a</td><td>open file for <strong>appending</strong>. the file is created if it does not exist.</td></tr><tr><td>ax</td><td>like 'a' but <strong>fails if path exists.</strong></td></tr><tr><td>a+</td><td>open file for <strong>reading and appen</strong>ding. the file is created if it does not exist.</td></tr><tr><td>ax+</td><td>open the file for <strong>reading and appending</strong>. the file is created if it does not exist.</td></tr></tbody></table>

Create a JavaScript file named "main.js" having the following code to open a file input.txt for reading and writing.

```javascript
var fs = require("fs");
// Asynchronous - Opening File  
console.log("Going to open file!");
fs.open('input.txt', 'r+', function (err, fd) {
    if (err) {
        return console.error(err);
    }
    console.log("File opened successfully!");
});  
```

Open the Node.js command prompt and run the main.js:

```bash
node main.js
```

<figure><img src="../.gitbook/assets/File system open file.png" alt=""><figcaption><p>File system Open file</p></figcaption></figure>

## Node.js File Information Method

Following is the syntax of the method to get file information.

```javascript
fs.stat(path, callback)
```

**Parameter explanation:**

* **a Path:** This is a string having a file name including the path.
* **Callback:** This is the callback function that gets two arguments (err, stats) where stats is an object of fs.Stats type.

| Method                    | Description                                      |
| ------------------------- | ------------------------------------------------ |
| stats.isfile()            | returns true if file type of a simple file.      |
| stats.isdirectory()       | returns true if file type of a directory.        |
| stats.isblockdevice()     | returns true if file type of a block device.     |
| stats.ischaracterdevice() | returns true if file type of a character device. |
| stats.issymboliclink()    | returns true if file type of a symbolic link.    |
| stats.isfifo()            | returns true if file type of a fifo.             |
| stats.issocket()          | returns true if file type of asocket.            |

Let's take an example to create a JavaScript file named main.js having the following code:

```javascript
var fs = require("fs");
console.log("Going to get file info!");
fs.stat('input.txt', function (err, stats) {
    if (err) {
        return console.error(err);
    }
    console.log(stats);
    console.log("Got file info successfully!");
    
    // Check file type  
    console.log("isFile ? " + stats.isFile());
    console.log("isDirectory ? " + stats.isDirectory());
});
```

Now open the Node.js command prompt and run the main.js

```bash
node main.js
```

<figure><img src="../.gitbook/assets/File system Information Method.png" alt=""><figcaption><p>File system Information Method</p></figcaption></figure>
