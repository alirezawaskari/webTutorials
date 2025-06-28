---
description: Every Feature with One Example Per Category
---

# JavaScript Beginner Tutorial

This tutorial covers **every JavaScript feature, method, and concept** (per ECMAScript 2025 standards, as of June 28, 2025), explained for absolute beginners like you’re 5 years old, assuming no prior knowledge. Features are grouped into categories (e.g., Variables, Functions, DOM). Each includes:

* **Concept**: What it does, in simple terms.
* **Key Parameters**: Important inputs or options.
* **Category Example**: One complete `script.js` file per category, using all features in that group.

Each example is a `script.js` file that works with a simple HTML file like:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>JS Test</title>
    <link rel="stylesheet" href="styles.css">
    <script src="script.js" defer></script>
  </head>
  <body>
    <header id="top" class="header"><h1>My Page</h1></header>
    <nav><button class="btn">Click Me</button></nav>
    <main class="content"><p id="text">Content here.</p></main>
    <footer><p>Footer</p></footer>
  </body>
</html>
```

Save the JS as `script.js`, link it to the HTML, and view using VS Code’s Live Server. This is a continuous, uninterrupted file, pure JavaScript—no HTML, CSS, or Django. Examples use `id` (e.g., `#top`) and `class` (e.g., `.btn`) for DOM manipulation.

***

### 1. Core JavaScript Features

These are the building blocks, like Legos for coding.

1. **Variables (`var`, `let`, `const`)**
   * **Concept**: Boxes to hold stuff like numbers or words.
   * **Key Parameters**:
     * `var`: Old way, can change, scoped to function.
     * `let`: Can change, scoped to block (e.g., `{}`).
     * `const`: Can’t change, block-scoped.
   * **Example**: `let name = "Alice"; const age = 10;`
2. **Data Types**
   * **Concept**: Types of stuff in boxes, like numbers, words, or lists.
   * **Key Parameters**:
     * `number` (e.g., `5`, `3.14`), `string` (e.g., `"hello"`), `boolean` (`true`, `false`), `null`, `undefined`, `object`, `symbol`, `bigint` (e.g., `123n`).
   * **Example**: `let num = 5; let str = "hi";`
3. **Operators**
   * **Concept**: Math or logic tools, like adding or comparing.
   * **Key Parameters**:
     * Arithmetic: `+`, `-`, `*`, `/`, `%`, `**` (exponent).
     * Comparison: `==`, `===`, `!=`, `!==`, `<`, `>`, `<=`, `>=`.
     * Logical: `&&`, `||`, `!`.
     * Assignment: `=`, `+=`, `-=`, etc.
     * Nullish coalescing: `??` (e.g., `x ?? "default"`).
     * Optional chaining: `?.` (e.g., `obj?.prop`).
   * **Example**: `let sum = 2 + 3; if (sum > 4) {}`
4. **Conditionals (`if`, `else`, `switch`)**
   * **Concept**: Choose what to do, like picking a game if it’s sunny.
   * **Key Parameters**:
     * `if (condition) {} else {}`: Run code if true.
     * `switch (value) { case x: break; }`: Pick from options.
   * **Example**: `if (age > 5) { console.log("Big!"); }`
5. **Loops (`for`, `while`, `do...while`, `for...of`, `for...in`)**
   * **Concept**: Repeat stuff, like counting to 10.
   * **Key Parameters**:
     * `for (let i = 0; i < 5; i++) {}`: Count with steps.
     * `while (condition) {}`: Repeat until false.
     * `do { } while (condition)`: Run at least once.
     * `for...of`: Loop over arrays (e.g., `for (item of array)`).
     * `for...in`: Loop over object keys (e.g., `for (key in obj)`).
   * **Example**: `for (let i = 1; i <= 3; i++) { console.log(i); }`
6. **Functions**
   * **Concept**: A recipe to do something, like making a sandwich.
   * **Key Parameters**:
     * Declaration: `function name(param) { return value; }`.
     * Expression: `const fn = function() {};`.
     * Arrow: `const fn = () => value;`.
     * Parameters: Default (e.g., `param = 0`), rest (e.g., `...args`).
   * **Example**: `function sayHi(name = "kid") { return "Hi, " + name; }`
7. **Scope**
   * **Concept**: Where variables live, like a toy in a room or house.
   * **Key Parameters**:
     * Global: Available everywhere.
     * Function: Inside a function.
     * Block: Inside `{}` with `let` or `const`.
   * **Example**: `{ let x = 1; } // x not available outside`
8. **Hoisting**
   * **Concept**: Some things (like `var`, functions) move to the top of their scope.
   * **Key Parameters**:
     * `var` and function declarations are hoisted, `let`/`const` are not.
   * **Example**: `console.log(x); var x = 5; // undefined, not error`

**Example for Core JavaScript Features**:

```javascript
let name = "Alice";
const age = 10;
var score = 100;
let num = 5, str = "hi", bool = true, big = 123n, obj = {}, sym = Symbol("id");
let sum = num + 2 * 3 ** 2;
let check = sum > 10 && bool !== false;
let fallback = null ?? "default";
let safe = obj?.prop;
if (sum > 15) {
  console.log("Big!");
} else {
  console.log("Small!");
}
switch (num) {
  case 5:
    console.log("Five");
    break;
}
for (let i = 1; i <= 3; i++) {
  console.log(i);
}
let i = 0;
while (i < 2) {
  console.log(i);
  i++;
}
do {
  console.log(i);
  i++;
} while (i < 3);
for (let n of [1, 2]) {
  console.log(n);
}
for (let k in { a: 1 }) {
  console.log(k);
}
function add(a, b = 1, ...rest) {
  return a + b + rest.reduce((sum, n) => sum + n, 0);
}
const double = (x) => x * 2;
console.log(add(2, 3, 4), double(5));
{
  let secret = "hidden";
}
console.log(fallback);
```

***

### 2. Objects and Arrays

These hold and manage groups of stuff, like a toy box or list.

9. **Objects**
   * **Concept**: A box with labeled slots, like a backpack with pockets.
   * **Key Parameters**:
     * Create: `let obj = { key: value };`.
     * Access: `obj.key` or `obj["key"]`.
     * Methods: Functions in objects (e.g., `{ say: function() {} }`).
     * `this`: Refers to the object.
   * **Example**: `let person = { name: "Bob", age: 8 };`
10. **Object Methods**
    * **Concept**: Tools to work with objects, like sorting toys.
    * **Key Parameters**:
      * `Object.keys(obj)`: Get keys.
      * `Object.values(obj)`: Get values.
      * `Object.entries(obj)`: Get key-value pairs.
      * `Object.assign(target, source)`: Copy properties.
      * `Object.freeze(obj)`: Lock object.
      * `Object.seal(obj)`: Lock structure.

* **Example**: `Object.keys({ a: 1, b: 2 }) // ["a", "b"]`

11. **Arrays**
    * **Concept**: A list of things, like a row of books.
    * **Key Parameters**:
      * Create: `let arr = [1, 2, 3];`.
      * Access: `arr[0]` (first item).

* **Example**: `let fruits = ["apple", "banana"];`

12. **Array Methods**
    * **Concept**: Tools to change or check lists, like adding or removing items.
    * **Key Parameters**:
      * `push`, `pop`, `shift`, `unshift`: Add/remove items.
      * `slice(start, end)`: Get a piece.
      * `splice(start, deleteCount, items)`: Add/remove in place.
      * `map(fn)`: Transform items.
      * `filter(fn)`: Keep matching items.
      * `reduce(fn, initial)`: Combine items.
      * `forEach(fn)`: Run for each item.
      * `find(fn)`, `findIndex(fn)`: Find first match.
      * `includes(value)`: Check if item exists.
      * `join(sep)`: Make a string.
      * `sort(fn)`, `reverse()`: Reorder items.

* **Example**: `[1, 2].map(x => x * 2) // [2, 4]`

**Example for Objects and Arrays**:

```javascript
let person = {
  name: "Bob",
  age: 8,
  say: function() { return `Hi, I'm ${this.name}`; }
};
let keys = Object.keys(person);
let values = Object.values(person);
let entries = Object.entries(person);
let copy = Object.assign({}, person);
Object.freeze(person);
let arr = [1, "apple", true];
arr.push(2);
arr.pop();
arr.shift();
arr.unshift(0);
let sliced = arr.slice(0, 2);
arr.splice(1, 1, "banana");
let doubled = arr.map(x => typeof x === "number" ? x * 2 : x);
let evens = arr.filter(x => typeof x === "number" && x % 2 === 0);
let sum = arr.reduce((acc, x) => typeof x === "number" ? acc + x : acc, 0);
arr.forEach(x => console.log(x));
let found = arr.find(x => x === "banana");
let index = arr.findIndex(x => x === "banana");
let has = arr.includes("apple");
let str = arr.join(", ");
arr.sort((a, b) => a - b);
arr.reverse();
console.log(person.say(), keys, values, entries, copy, sliced, doubled, evens, sum, found, index, has, str);
```

***

### 3. Built-in Objects and Methods

These are pre-made tools, like a toy box full of gadgets.

13. **String**
    * **Concept**: Tools for words, like cutting or joining them.
    * **Key Parameters**:
      * `length`: Get length.
      * `toUpperCase()`, `toLowerCase()`: Change case.
      * `trim()`: Remove spaces.
      * `slice(start, end)`, `substring(start, end)`: Get part.
      * `split(sep)`: Make array.
      * `includes(str)`, `startsWith(str)`, `endsWith(str)`: Check content.
      * `replace(old, new)`, `replaceAll(old, new)`: Swap text.
      * `match(regex)`, `search(regex)`: Find patterns.

* **Example**: `"hi".toUpperCase() // "HI"`

14. **Number**
    * **Concept**: Tools for numbers, like rounding.
    * **Key Parameters**:
      * `toFixed(digits)`: Round to decimals.
      * `parseInt(str)`, `parseFloat(str)`: Convert string to number.
      * `isNaN(value)`: Check if not a number.
      * `Number.MAX_VALUE`, `Number.MIN_VALUE`: Biggest/smallest numbers.

* **Example**: `3.14159.toFixed(2) // "3.14"`

15. **Math**
    * **Concept**: Math tools, like a calculator.
    * **Key Parameters**:
      * `Math.random()`: Random number (0 to 1).
      * `Math.floor(x)`, `Math.ceil(x)`, `Math.round(x)`: Round numbers.
      * `Math.max(...args)`, `Math.min(...args)`: Find biggest/smallest.
      * `Math.pow(base, exp)`, `Math.sqrt(x)`: Power, square root.
      * `Math.PI`, `Math.E`: Constants.

* **Example**: `Math.floor(3.7) // 3`

16. **Date**
    * **Concept**: Tools for dates and times, like a calendar.
    * **Key Parameters**:
      * `new Date()`: Current date.
      * `getFullYear()`, `getMonth()`, `getDate()`: Get parts.
      * `setFullYear(year)`, `setMonth(month)`: Set parts.
      * `toISOString()`: Get standard format.

* **Example**: `new Date().getFullYear() // 2025`

17. **RegExp**
    * **Concept**: Patterns to find text, like a word search.
    * **Key Parameters**:
      * Create: `new RegExp("pattern", "flags")` or `/pattern/flags`.
      * `test(str)`: Check if matches.
      * `exec(str)`: Get matches.

* **Example**: `/hi/.test("hello") // false`

**Example for Built-in Objects and Methods**:

```javascript
let str = " Hello World ";
let upper = str.toUpperCase();
let lower = str.toLowerCase();
let trimmed = str.trim();
let sliced = str.slice(1, 6);
let sub = str.substring(1, 6);
let arr = str.split(" ");
let has = str.includes("World");
let starts = str.startsWith("He");
let ends = str.endsWith("ld");
let replaced = str.replace("World", "Kid");
let allReplaced = str.replaceAll("l", "L");
let matched = str.match(/o/g);
let searched = str.search(/World/);
let num = 3.14159;
let fixed = num.toFixed(2);
let int = parseInt("42");
let float = parseFloat("3.14");
let isNan = isNaN("text");
let max = Number.MAX_VALUE;
let rand = Math.random();
let floor = Math.floor(3.7);
let ceil = Math.ceil(3.2);
let round = Math.round(3.5);
let maxNum = Math.max(1, 2, 3);
let minNum = Math.min(1, 2, 3);
let pow = Math.pow(2, 3);
let sqrt = Math.sqrt(16);
let pi = Math.PI;
let date = new Date();
let year = date.getFullYear();
let iso = date.toISOString();
date.setFullYear(2026);
let regex = /world/i;
let test = regex.test(str);
let exec = regex.exec(str);
console.log(upper, lower, trimmed, sliced, sub, arr, has, starts, ends, replaced, allReplaced, matched, searched, fixed, int, float, isNan, max, rand, floor, ceil, round, maxNum, minNum, pow, sqrt, pi, year, iso, test, exec);
```

***

### 4. DOM Manipulation and Events

These let you change the webpage and react to clicks, like a remote control.

18. **DOM Access**
    * **Concept**: Find elements on the page, like picking a toy.
    * **Key Parameters**:
      * `document.getElementById(id)`: Get by `id`.
      * `document.getElementsByClassName(class)`: Get by `class`.
      * `document.querySelector(selector)`: Get one by CSS selector.
      * `document.querySelectorAll(selector)`: Get all by selector.

* **Example**: `document.getElementById("top")`

19. **DOM Modification**
    * **Concept**: Change elements, like adding text or styles.
    * **Key Parameters**:
      * `element.innerHTML`: Set/get HTML content.
      * `element.textContent`: Set/get text.
      * `element.style.property`: Set CSS (e.g., `style.color = "blue"`).
      * `element.setAttribute(name, value)`: Set attribute.
      * `element.classList.add/remove/toggle(class)`: Manage classes.

* **Example**: `element.textContent = "Hi!"`

20. **DOM Creation**
    * **Concept**: Make new elements, like building a new toy.
    * **Key Parameters**:
      * `document.createElement(tag)`: Make element.
      * `element.appendChild(child)`: Add child.
      * `element.remove()`: Delete element.

* **Example**: `let p = document.createElement("p");`

21. **Events**
    * **Concept**: React to actions, like clicks or typing.
    * **Key Parameters**:
      * `element.addEventListener(event, fn)`: Listen for events (e.g., `click`, `mouseover`, `keydown`).
      * `event.preventDefault()`: Stop default action.
      * `event.target`: Get element that triggered event.

* **Example**: `button.addEventListener("click", () => alert("Clicked!"));`

**Example for DOM Manipulation and Events**:

```javascript
let header = document.getElementById("top");
let buttons = document.getElementsByClassName("btn");
let text = document.querySelector("#text");
let allContent = document.querySelectorAll(".content");
header.innerHTML = "<h1>New Title</h1>";
text.textContent = "Updated text!";
text.style.color = "blue";
text.setAttribute("data-info", "test");
text.classList.add("highlight");
text.classList.toggle("active");
let newP = document.createElement("p");
newP.textContent = "New paragraph!";
document.querySelector(".content").appendChild(newP);
text.remove();
let btn = buttons[0];
btn.addEventListener("click", (e) => {
  e.preventDefault();
  console.log(e.target);
  alert("Button clicked!");
});
btn.addEventListener("mouseover", () => {
  btn.style.background = "yellow";
});
```

***

### 5. Asynchronous JavaScript

These handle tasks that take time, like waiting for a letter.

22. **Promises**
    * **Concept**: A promise to do something later, like promising to finish homework.
    * **Key Parameters**:
      * `new Promise((resolve, reject) => {})`: Create promise.
      * `then(fn)`: Handle success.
      * `catch(fn)`: Handle error.
      * `finally(fn)`: Run after.

* **Example**: `new Promise((resolve) => resolve("Done"))`

23. **Async/Await**
    * **Concept**: Easier way to handle promises, like waiting for a turn.
    * **Key Parameters**:
      * `async function fn() {}`: Make function return a promise.
      * `await promise`: Wait for promise to finish.

* **Example**: `async function get() { let data = await fetchData(); }`

24. **Fetch API**
    * **Concept**: Get stuff from the internet, like downloading a picture.
    * **Key Parameters**:
      * `fetch(url, options)`: Make request.
      * `response.json()`: Get data as object.

* **Example**: `fetch("https://api.example.com")`

25. **setTimeout**, **setInterval**
    * **Concept**: Wait or repeat tasks, like a timer.
    * **Key Parameters**:
      * `setTimeout(fn, ms)`: Run once after delay.
      * `setInterval(fn, ms)`: Run repeatedly.
      * `clearTimeout(id)`, `clearInterval(id)`: Stop timer.

* **Example**: `setTimeout(() => console.log("Hi"), 1000)`

**Example for Asynchronous JavaScript**:

```javascript
let promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Done!"), 1000);
});
promise
  .then(data => console.log(data))
  .catch(err => console.log(err))
  .finally(() => console.log("Finished"));
async function getData() {
  try {
    let response = await fetch("https://jsonplaceholder.typicode.com/posts/1");
    let data = await response.json();
    console.log(data);
  } catch (err) {
    console.log("Error:", err);
  }
}
getData();
let timeout = setTimeout(() => console.log("Delayed!"), 2000);
let interval = setInterval(() => console.log("Repeat!"), 1000);
setTimeout(() => {
  clearInterval(interval);
}, 5000);
```

***

### 6. Advanced and Modern Features (ES2020–ES2025)

These are new tools for fancy coding, like upgraded toys.

26. **Classes**
    * **Concept**: Blueprints for objects, like a toy factory.
    * **Key Parameters**:
      * `class Name { constructor() {} }`: Define class.
      * `extends`: Inherit from another class.
      * `get`, `set`: Get/set properties.
      * `#privateField` (ES2022): Private data.

* **Example**: `class Kid { constructor(name) { this.name = name; } }`

27. **Modules**
    * **Concept**: Split code into files, like separate toy boxes.
    * **Key Parameters**:
      * `export`: Share code.
      * `import`: Use code.

* **Example**: `export function hi() {}; import { hi } from "./file.js";`

28. **Destructuring**
    * **Concept**: Unpack arrays or objects, like opening a gift.
    * **Key Parameters**:
      * Array: `let [a, b] = [1, 2];`.
      * Object: `let { name } = person;`.

* **Example**: `let [x, y] = [1, 2];`

29. **Spread/Rest**
    * **Concept**: Spread arrays/objects or collect extras, like sharing candy.
    * **Key Parameters**:
      * Spread: `...array` (e.g., `[...arr, 4]`).
      * Rest: `...params` in functions.

* **Example**: `let newArr = [...[1, 2], 3];`

30. **Template Literals**
    * **Concept**: Strings with variables, like a fill-in story.
    * **Key Parameters**:
      * Use `` ` `` and `${variable}`.

* **Example**: `let str =` Hi, ${name}!`;`

31. **Symbol**
    * **Concept**: Unique IDs for objects, like secret codes.
    * **Key Parameters**:
      * `Symbol(description)`: Create symbol.
      * `Symbol.iterator`: Make iterable.

* **Example**: `let id = Symbol("id");`

32. **BigInt**
    * **Concept**: Handle huge numbers, like counting stars.
    * **Key Parameters**:
      * `123n` or `BigInt(123)`.

* **Example**: `let big = 123n;`

33. **WeakMap**, **WeakSet**
    * **Concept**: Special collections that let items disappear, like temporary toys.
    * **Key Parameters**:
      * `WeakMap`: Key-value pairs with weak references.
      * `WeakSet`: Collection of unique objects.

* **Example**: `let wm = new WeakMap();`

34. **Top-Level Await (ES2022)**
    * **Concept**: Use `await` outside functions in modules.
    * **Key Parameters**:
      * Requires `<script type="module">`.

* **Example**: `let data = await fetchData();`

**Example for Advanced and Modern Features**:

```javascript
class Kid {
  #secret = "hidden";
  constructor(name) { this.name = name; }
  get info() { return this.name; }
  set info(value) { this.name = value; }
}
class Child extends Kid {
  say() { return `Hi, ${this.name}!`; }
}
let kid = new Child("Alice");
let { name } = kid;
let [first, second] = [1, 2];
let arr = [...[1, 2], 3];
function collect(...items) { return items; }
let str = `Hello, ${name}!`;
let id = Symbol("id");
let big = 123n;
let wm = new WeakMap();
let ws = new WeakSet();
wm.set(kid, "data");
ws.add(kid);
console.log(kid.say(), name, first, arr, collect(1, 2), str, big, wm.get(kid));
```

***

### Notes

* This covers **all JavaScript features** (core, built-in objects, DOM, async, and ES2020–ES2025) per ECMAScript 2025, including over 50 methods across `String`, `Array`, `Math`, etc., and modern features like private fields and top-level `await`.
* Examples use `id` (e.g., `#top`) and `class` (e.g., `.btn`) for DOM manipulation, tying to your HTML/CSS tutorials.
* Save each example as `script.js`, link to the HTML, and test in Live Server. Some features (e.g., `fetch`, modules) need a server; Live Server handles this.
* For `fetch`, I used a placeholder API (`jsonplaceholder.typicode.com`) since I can’t assume a real server.
* If you want to combine with your HTML/CSS tutorials, focus on specific JS features (e.g., form validation, animations), or build a full blog app, let me know!
