---
description: From Zero to Expert
---

# TypeScript Pro Course

This course is for beginners with HTML, CSS, basic JavaScript (variables, functions, arrays), and some React knowledge. You’ll learn **TypeScript**, a JavaScript superset that adds static types for safer, more maintainable code. By the end, you’ll master TypeScript’s core and advanced features, integrate it with React and Vite, and build a project to solidify your skills. This is a hands-on, no-BS guide to make you a TypeScript pro.

**What You’ll Learn**:

1. TypeScript basics (types, interfaces, functions).
2. Advanced features (generics, unions, type narrowing).
3. Integration with React and Vite.
4. Best practices and debugging.
5. Project: A React to-do list app with TypeScript.

**Tools Needed**:

* **Node.js**: [Download LTS](https://nodejs.org) (installs `npm`).
* **VS Code**: [Free download](https://code.visualstudio.com/) with TypeScript support.
* A browser (Chrome recommended).
* Optional: [TypeScript Playground](https://www.typescriptlang.org/play) for testing.

**How to Use This Document**:

* Save as `TypeScript_Pro_Course.md` or convert to PDF (e.g., VS Code with “Markdown PDF” extension).
* Follow each section, code the examples, and do the exercises.
* Set up a project (Part 5) to code along.
* Build the project in Part 6 to apply your skills.
* Refer to resources for extra learning.

**Time Commitment**: \~15-20 hours (spread over days/weeks).

***

### Part 1: TypeScript Basics

#### 1.1 What is TypeScript?

TypeScript is a **JavaScript superset** that adds static types, catching errors at compile time (before running the code).

* **Why TypeScript?**
  * Prevents bugs (e.g., passing a string to a number-based function).
  * Improves code readability and refactoring.
  * Essential for large React/Next.js projects.
  * Used by companies like Microsoft, Slack, and Airbnb.
* **Example**: Catch a bug where a function expects a number but gets a string.

#### 1.2 Basic Types

Add types to variables, functions, and objects.

**Example**:

```typescript
// src/index.ts
let name: string = 'Dude';
let age: number = 25;
let isCool: boolean = true;

function greet(name: string): string {
  return `Yo, ${name}!`;
}

console.log(greet(name)); // Yo, Dude!
// console.log(greet(123)); // Error: Argument of type 'number' is not assignable
```

* Types: `string`, `number`, `boolean`, etc.
* Run: `npx tsc index.ts` to compile to JavaScript.

**Exercise**:

1. Create a variable `score: number` and a function `double(num: number): number`.
2. Test with a string to see the error.

**Answer**:

```typescript
// src/index.ts
let score: number = 100;

function double(num: number): number {
  return num * 2;
}

console.log(double(score)); // 200
// console.log(double('10')); // Error
```

#### 1.3 Interfaces and Objects

Define object shapes with interfaces.

**Example**:

```typescript
interface User {
  name: string;
  age: number;
}

const user: User = {
  name: 'Dude',
  age: 25,
};

function printUser(user: User): void {
  console.log(`${user.name}, ${user.age}`);
}

printUser(user);
// printUser({ name: 'Alice' }); // Error: Missing age
```

**Exercise**:

1. Create an interface `Product` with `name: string` and `price: number`.
2. Write a function to log a product.

**Answer**:

```typescript
interface Product {
  name: string;
  price: number;
}

const product: Product = {
  name: 'Laptop',
  price: 999,
};

function logProduct(product: Product): void {
  console.log(`${product.name}: $${product.price}`);
}

logProduct(product);
```

***

### Part 2: Advanced TypeScript

#### 2.1 Unions and Type Narrowing

Use unions (`|`) for multiple types and narrow with checks.

**Example**:

```typescript
function printId(id: number | string): void {
  if (typeof id === 'string') {
    console.log(id.toUpperCase());
  } else {
    console.log(id);
  }
}

printId('abc'); // ABC
printId(123); // 123
```

**Exercise**:

1. Create a function that accepts `string | boolean` and logs differently based on type.

**Answer**:

```typescript
function printValue(value: string | boolean): void {
  if (typeof value === 'string') {
    console.log(`String: ${value}`);
  } else {
    console.log(`Boolean: ${value}`);
  }
}

printValue('test'); // String: test
printValue(true); // Boolean: true
```

#### 2.2 Generics

Create reusable components with generics.

**Example**:

```typescript
function identity<T>(value: T): T {
  return value;
}

console.log(identity<string>('Dude')); // Dude
console.log(identity<number>(123)); // 123
```

**Exercise**:

1. Create a generic function `getFirst<T>` that returns the first item of an array.

**Answer**:

```typescript
function getFirst<T>(arr: T[]): T {
  return arr[0];
}

console.log(getFirst<number>([1, 2, 3])); // 1
console.log(getFirst<string>(['a', 'b', 'c'])); // a
```

***

### Part 3: TypeScript with React

Use TypeScript in a React + Vite project.

**Setup**:

```bash
npm create vite@latest ts-react-app -- --template react-ts
cd ts-react-app
npm install
npm run dev
```

**Example (src/App.tsx)**:

```tsx
import { useState } from 'react';

interface Props {
  title: string;
}

const App: React.FC<Props> = ({ title }) => {
  const [count, setCount] = useState<number>(0);

  return (
    <div>
      <h1>{title}</h1>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
};

export default App;
```

**Exercise**:

1. Create a `Greeting.tsx` component with a `name: string` prop and a `message: string` state.

**Answer**:

```tsx
// src/Greeting.tsx
import { useState } from 'react';

interface Props {
  name: string;
}

const Greeting: React.FC<Props> = ({ name }) => {
  const [message, setMessage] = useState<string>('');

  return (
    <div>
      <input
        value={message}
        onChange={(e) => setMessage(e.target.value)}
        placeholder="Type a message"
      />
      <p>
        Hello, {name}! {message}
      </p>
    </div>
  );
};

export default Greeting;
```

```tsx
// src/App.tsx
import Greeting from './Greeting';

const App: React.FC = () => {
  return (
    <div>
      <Greeting name="Dude" />
    </div>
  );
};

export default App;
```

***

### Part 4: TypeScript with Vite

Configure Vite for TypeScript.

**vite.config.ts**:

```typescript
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

export default defineConfig({
  plugins: [react()],
});
```

**tsconfig.json** (auto-generated):

```json
{
  "compilerOptions": {
    "target": "ESNext",
    "useDefineForClassFields": true,
    "lib": ["DOM", "DOM.Iterable", "ESNext"],
    "allowJs": false,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "module": "ESNext",
    "moduleResolution": "Node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx"
  },
  "include": ["src"]
}
```

**Exercise**:

1. Add a TypeScript interface to a Vite + React component.

***

### Part 5: Project Setup

1. **Install Node.js**: [Download LTS](https://nodejs.org).
2.  **Create Project**:

    ```bash
    npm create vite@latest ts-react-app -- --template react-ts
    cd ts-react-app
    npm install
    npm run dev
    ```
3. Open `http://localhost:5173`.

**Structure**:

```
ts-react-app/
├── src/
│   ├── main.tsx
│   ├── App.tsx
│   ├── index.css
├── public/
├── vite.config.ts
├── tsconfig.json
├── package.json
```

***

### Part 6: Project: React To-Do List with TypeScript

**Goal**: Build a typed to-do list app with Vite and TypeScript.

**Code (src/App.tsx)**:

```tsx
import { useState, useEffect } from 'react';
import './App.css';

interface Todo {
  id: number;
  text: string;
  done: boolean;
}

const App: React.FC = () => {
  const [todos, setTodos] = useState<Todo[]>(() => {
    const saved = localStorage.getItem('todos');
    return saved ? JSON.parse(saved) : [];
  });
  const [input, setInput] = useState<string>('');

  useEffect(() => {
    localStorage.setItem('todos', JSON.stringify(todos));
  }, [todos]);

  const addTodo = () => {
    if (input.trim()) {
      setTodos([...todos, { id: Date.now(), text: input, done: false }]);
      setInput('');
    }
  };

  const toggleTodo = (id: number) => {
    setTodos(
      todos.map((todo) =>
        todo.id === id ? { ...todo, done: !todo.done } : todo
      )
    );
  };

  const deleteTodo = (id: number) => {
    setTodos(todos.filter((todo) => todo.id !== id));
  };

  return (
    <div className="todo-app">
      <h1>To-Do List</h1>
      <div className="input-container">
        <input
          value={input}
          onChange={(e: React.ChangeEvent<HTMLInputElement>) =>
            setInput(e.target.value)
          }
          placeholder="Add a task"
          onKeyPress={(e: React.KeyboardEvent) =>
            e.key === 'Enter' && addTodo()
          }
        />
        <button onClick={addTodo}>Add</button>
      </div>
      <ul>
        {todos.map((todo) => (
          <li
            key={todo.id}
            className={todo.done ? 'done' : ''}
            onClick={() => toggleTodo(todo.id)}
          >
            {todo.text}
            <button
              className="delete-btn"
              onClick={(e: React.MouseEvent) => {
                e.stopPropagation();
                deleteTodo(todo.id);
              }}
            >
              Delete
            </button>
          </li>
        ))}
      </ul>
    </div>
  );
};

export default App;
```

**CSS (src/App.css)**:

```css
.todo-app {
  max-width: 500px;
  margin: 20px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.input-container {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

input {
  flex: 1;
  padding: 8px;
  font-size: 16px;
}

button {
  padding: 8px 16px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  border-bottom: 1px solid #eee;
  cursor: pointer;
}

.done {
  text-decoration: line-through;
  color: #888;
}

.delete-btn {
  background-color: #dc3545;
}

.delete-btn:hover {
  background-color: #c82333;
}
```

**Steps**:

1. Set up the project (Part 5).
2. Replace `src/App.tsx` and `src/App.css` with the code above.
3. Run `npm run dev`.

**Exercises**:

1. Add a `Clear All` button with proper types.
2. Create an interface for a `filter` state (e.g., `'all' | 'active' | 'completed'`).
3. Add type safety for an API fetch.

**Answer (Clear All)**:

```tsx
const clearAll = () => setTodos([]);
// Add to JSX:
<button onClick={clearAll}>Clear All</button>
```

***

### Part 7: Pro Practices

#### 7.1 Debugging

* Use VS Code’s TypeScript support for error highlighting.
* Check `tsc --noEmit` for type errors.
* Use Chrome DevTools for runtime issues.

#### 7.2 Best Practices

* Use interfaces over types for objects.
* Enable `strict` mode in `tsconfig.json`.
* Avoid `any` type; be specific.

#### 7.3 Deployment

* Build: `npm run build`.
* Deploy `dist/` to Vercel or Netlify.

***

### Part 8: Next Steps

1. **Advanced TypeScript**: Explore mapped types, conditional types.
2. **Integrations**: Use with Next.js, Tailwind, Redux.
3. **Tools**: Learn `ts-jest` for testing.
4. **Projects**: Build a typed portfolio or dashboard.

**Resources**:

* [TypeScript Docs](https://www.typescriptlang.org)
* X’s #TypeScript tag for community tips

***

### Conclusion

You’ve mastered TypeScript: basic types, interfaces, generics, and React integration. The to-do list project applies these skills with type safety. Keep practicing by extending the project or building new typed apps. Search X for #TypeScript if you’re stuck, or ask me for help!
