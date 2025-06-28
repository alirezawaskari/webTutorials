---
description: Every Feature with One Example Per Category
---

# Node.js Beginner Tutorial

This tutorial covers **every core Node.js feature, module, and concept** (per Node.js 20.x standards, as of June 28, 2025), explained for absolute beginners like you’re 5 years old, assuming no prior knowledge. Features are grouped into categories (e.g., Core Features, File System, Networking). Each includes:

* **Concept**: What it does, in simple terms.
* **Key Components**: Important parts, methods, or options.
* **Category Example**: One complete `app.js` file per category, showing all features in that group.

Each example is a `app.js` file, runnable by installing Node.js 20.x (download from nodejs.org, then run `node app.js` in a terminal from your project folder). For HTTP examples, a simple `index.html` is referenced (with `id` and `class` for consistency with your HTML/CSS/JS tutorials). Save the HTML in the same folder and test with a browser (e.g., `http://localhost:3000`). This is pure Node.js—no HTML, CSS, or frontend frameworks, just server-side JavaScript for your blog app backend.

**Setup**:

1. Install Node.js 20.x (nodejs.org).
2. Create a folder (e.g., `my-blog`).
3. Save each example as `app.js`.
4. Run `node app.js` in terminal (VS Code: open terminal with Ctrl+\`).
5. For HTTP examples, create `index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Node.js Demo</title>
  <style>
    #top { background: blue; color: white; padding: 10px; }
    .content { margin: 20px; }
  </style>
</head>
<body>
  <header id="top"><h1>My Blog</h1></header>
  <main class="content"><p>Welcome!</p></main>
</body>
</html>
```

***

### 1. Core Node.js Features

These are the main tools for Node.js, like the basic parts of a toy car.

1. **Node.js Runtime**
   * **Concept**: A program that runs JavaScript outside browsers, like a computer for your code.
   * **Key Components**:
     * **V8 Engine**: Runs JavaScript.
     * **Event Loop**: Handles tasks one by one.
     * **Non-Blocking I/O**: Does many things at once (e.g., reading files without waiting).
2. **Modules (CommonJS)**
   * **Concept**: Split code into files, like toy boxes for different parts.
   * **Key Components**:
     * `require(module)`: Import code (e.g., `require("fs")`).
     * `module.exports`: Share code (e.g., `module.exports = fn`).
     * **Built-in Modules**: `fs`, `http`, `path`, etc.
3. **Global Objects**
   * **Concept**: Tools always available, like a toolbox you don’t need to open.
   * **Key Components**:
     * `console`: Print messages (e.g., `console.log("Hi")`).
     * `process`: Info about your program (e.g., `process.argv` for arguments).
     * `setTimeout`, `setInterval`: Delay or repeat tasks.
4. **Events (EventEmitter)**
   * **Concept**: React to things happening, like a bell ringing when a task is done.
   * **Key Components**:
     * `EventEmitter`: Create custom events.
     * `on(event, fn)`: Listen for events.
     * `emit(event)`: Trigger events.

**Example for Core Node.js Features**:

```javascript
// app.js
const { EventEmitter } = require("events");
console.log("Starting Node.js!");
console.log(process.argv);
setTimeout(() => console.log("Delayed message!"), 1000);
let interval = setInterval(() => console.log("Repeating..."), 2000);
setTimeout(() => clearInterval(interval), 5000);
const myEmitter = new EventEmitter();
myEmitter.on("greet", (name) => console.log(`Hello, ${name}!`));
myEmitter.emit("greet", "Alice");
const myModule = require("./myModule.js");
console.log(myModule.sayHi());
```

// myModule.js (save in same folder)

```javascript
module.exports = {
  sayHi: () => "Hi from module!"
};
```

***

### 2. File System Operations

These let you work with files, like reading or writing in a notebook.

5. **File System (`fs`)**
   * **Concept**: Read, write, or manage files, like opening a book or saving a note.
   * **Key Components**:
     * `fs.readFile(path, encoding, callback)`: Read file.
     * `fs.writeFile(path, data, callback)`: Write file.
     * `fs.appendFile(path, data, callback)`: Add to file.
     * `fs.unlink(path, callback)`: Delete file.
     * `fs.readdir(path, callback)`: List files in folder.
     * **Promises API**: `fs.promises` for `async/await` (e.g., `fs.promises.readFile`).
6. **Path Handling (`path`)**
   * **Concept**: Work with file paths, like finding the right folder.
   * **Key Components**:
     * `path.join(...segments)`: Build paths (e.g., `path.join("folder", "file.txt")`).
     * `path.resolve()`: Get absolute path.
     * `path.extname(path)`: Get file extension (e.g., `.txt`).
     * `path.basename(path)`: Get file name.

**Example for File System Operations**:

```javascript
// app.js
const fs = require("fs").promises;
const path = require("path");
async function manageFiles() {
  try {
    const filePath = path.join(__dirname, "note.txt");
    await fs.writeFile(filePath, "Hello, Node.js!");
    await fs.appendFile(filePath, "\nMore text!");
    const data = await fs.readFile(filePath, "utf8");
    console.log("File content:", data);
    const files = await fs.readdir(__dirname);
    console.log("Files in folder:", files);
    console.log("File extension:", path.extname(filePath));
    console.log("File name:", path.basename(filePath));
    await fs.unlink(filePath);
    console.log("File deleted!");
  } catch (err) {
    console.error("Error:", err);
  }
}
manageFiles();
```

***

### 3. Networking and HTTP

These let Node.js talk to the internet or serve websites, like a mail carrier.

7. **HTTP Server (`http`)**
   * **Concept**: Create a web server to send pages, like opening a store.
   * **Key Components**:
     * `http.createServer((req, res) => {})`: Make server.
     * `req`: Request info (e.g., `req.url`, `req.method`).
     * `res`: Response (e.g., `res.write()`, `res.end()`).
     * `listen(port)`: Start server.
8. **URL Parsing (`url`)**
   * **Concept**: Break down web addresses, like reading a map.
   * **Key Components**:
     * `url.parse(urlString)`: Split URL into parts (e.g., path, query).
     * `new URL(urlString)`: Modern way to parse URLs.
     * `url.pathname`, `url.searchParams`: Get specific parts.
9. **Query Strings (`querystring`)**
   * **Concept**: Handle URL data, like reading notes in a web address (e.g., `?name=Alice`).
   * **Key Components**:
     * `querystring.parse(str)`: Turn query string into object.
     * `querystring.stringify(obj)`: Turn object into query string.

**Example for Networking and HTTP**:

```javascript
// app.js
const http = require("http");
const url = require("url");
const querystring = require("querystring");
const fs = require("fs").promises;
const server = http.createServer(async (req, res) => {
  const parsedUrl = url.parse(req.url, true);
  const query = querystring.parse(parsedUrl.query);
  if (parsedUrl.pathname === "/") {
    res.writeHead(200, { "Content-Type": "text/html" });
    try {
      const html = await fs.readFile("index.html", "utf8");
      res.end(html.replace("Welcome!", `Welcome, ${query.name || "Guest"}!`));
    } catch (err) {
      res.writeHead(500);
      res.end("Server Error");
    }
  } else {
    res.writeHead(404);
    res.end("Not Found");
  }
});
server.listen(3000, () => console.log("Server running on http://localhost:3000"));
```

***

### 4. Advanced Node.js Features

These are extra tools for bigger projects, like fancy parts for your toy car.

10. **Streams**
    * **Concept**: Handle big data in chunks, like sipping a drink through a straw.
    * **Key Components**:
      * `Readable`: Read data (e.g., `fs.createReadStream`).
      * `Writable`: Write data (e.g., `fs.createWriteStream`).
      * `pipe(dest)`: Connect streams.
      * `Transform`: Modify data.
11. **Child Processes**
    * **Concept**: Run other programs, like asking a friend to do a task.
    * **Key Components**:
      * `child_process.exec(command)`: Run command (e.g., `ls`).
      * `child_process.spawn(command, args)`: Run command with streaming.
      * `child_process.fork(module)`: Run Node.js script.
12. **Buffers**
    * **Concept**: Handle raw data, like a box for binary bits.
    * **Key Components**:
      * `Buffer.from(data)`: Create buffer.
      * `buffer.toString(encoding)`: Convert to text.
      * `buffer.write(data)`: Write to buffer.
13. **Async Hooks**
    * **Concept**: Track async tasks, like watching where your toys go.
    * **Key Components**:
      * `async_hooks.createHook(callbacks)`: Monitor async operations.
      * `asyncId`: Unique ID for async tasks.

**Example for Advanced Node.js Features**:

```javascript
// app.js
const fs = require("fs");
const { Transform } = require("stream");
const { exec } = require("child_process");
const asyncHooks = require("async_hooks");
const readStream = fs.createReadStream("input.txt");
const writeStream = fs.createWriteStream("output.txt");
const transform = new Transform({
  transform(chunk, encoding, callback) {
    callback(null, chunk.toString().toUpperCase());
  }
});
readStream.pipe(transform).pipe(writeStream);
writeStream.on("finish", () => console.log("File transformed!"));
const buffer = Buffer.from("Hello, Buffer!");
console.log(buffer.toString("utf8"));
exec("echo Hello from shell", (err, stdout) => {
  if (err) console.error(err);
  console.log(stdout);
});
const hook = asyncHooks.createHook({
  init(asyncId) { console.log(`Async task ${asyncId} started`); }
});
hook.enable();
setTimeout(() => console.log("Async task example"), 1000);
```

***

### 5. Node.js Utilities and Modules

These are helper tools for common tasks, like a Swiss Army knife.

14. **OS (`os`)**
    * **Concept**: Get info about the computer, like checking its name or memory.
    * **Key Components**:
      * `os.platform()`: Get OS (e.g., `linux`, `win32`).
      * `os.cpus()`: Get CPU info.
      * `os.totalmem()`, `os.freemem()`: Memory stats.
15. **Crypto (`crypto`)**
    * **Concept**: Secure data, like locking a secret message.
    * **Key Components**:
      * `crypto.createHash(algorithm)`: Create hash (e.g., `sha256`).
      * `crypto.randomBytes(size)`: Generate random data.
      * `crypto.createHmac(algorithm, key)`: Secure message authentication.
16. **Util (`util`)**
    * **Concept**: Extra tools for coding, like a helper robot.
    * **Key Components**:
      * `util.promisify(fn)`: Turn callback to promise.
      * `util.format(str, ...args)`: Format strings.
      * `util.inspect(obj)`: Print objects nicely.
17. **NPM (Node Package Manager)**
    * **Concept**: Install extra tools, like downloading new toys.
    * **Key Components**:
      * `npm init`: Create `package.json`.
      * `npm install package`: Add package (e.g., `npm install express`).
      * `package.json`: Project settings.

**Example for Utilities and Modules**:

```javascript
// app.js
const os = require("os");
const crypto = require("crypto");
const util = require("util");
const fs = require("fs");
const readdir = util.promisify(fs.readdir);
console.log("OS:", os.platform());
console.log("CPUs:", os.cpus().length);
console.log("Free Memory:", os.freemem());
const hash = crypto.createHash("sha256").update("secret").digest("hex");
console.log("Hash:", hash);
const random = crypto.randomBytes(16).toString("hex");
console.log("Random:", random);
const hmac = crypto.createHmac("sha256", "key").update("data").digest("hex");
console.log("HMAC:", hmac);
console.log(util.format("Hello, %s!", "Node"));
async function listFiles() {
  const files = await readdir(__dirname);
  console.log("Files:", files);
}
listFiles();
```

***

### Notes

* This covers **all core Node.js features and modules** (17 total) per Node.js 20.x, including runtime, modules, file system, HTTP, streams, and utilities, suitable for your blog app backend.
* Examples are `app.js` files, runnable with `node app.js`. HTTP examples serve `index.html` (with `id` and `class`) to tie to your HTML/CSS/JS tutorials.
* For HTTP, access `http://localhost:3000` in a browser. File system examples create/delete `note.txt` or read `index.html`.
* Create `myModule.js` for the Core Features example and `input.txt` for Streams (with any text, e.g., “test”).
* NPM example assumes basic usage; run `npm init -y` to create `package.json` if needed.
* If you want to integrate with your HTML/CSS/JS tutorials, add frameworks (e.g., Express for Node.js), or build a full blog backend, let me know!
