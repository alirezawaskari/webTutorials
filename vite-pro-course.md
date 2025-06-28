---
description: From Zero to Expert
---

# Vite Pro Course

### Introduction

This course is for beginners with HTML, CSS, basic JavaScript (variables, functions, arrays), and some React knowledge. You’ll learn **Vite**, a fast, modern build tool and development server for web projects. Vite is designed for speed, simplicity, and developer experience, making it a go-to for React, Vue, and other frameworks. By the end, you’ll master Vite’s core and advanced features, configure it for a React app, and build a project to solidify your skills. This is a hands-on, no-BS guide to make you a Vite pro.

**What You’ll Learn**:

1. Vite basics (setup, development server, builds).
2. Configuring Vite for React and TypeScript.
3. Advanced features (plugins, code splitting, environment variables).
4. Optimization and deployment.
5. Project: A React to-do list app with Vite.

**Tools Needed**:

* **Node.js**: [Download LTS](https://nodejs.org) (installs `npm`).
* **VS Code**: [Free download](https://code.visualstudio.com/).
* A browser (Chrome recommended).

**How to Use This Document**:

* Save as `Vite_Pro_Course.md` or convert to PDF (e.g., VS Code with “Markdown PDF” extension).
* Follow each section, code the examples, and do the exercises.
* Set up a Vite project (Part 5) to code along.
* Build the project in Part 6 to apply your skills.
* Refer to resources for extra learning.

**Time Commitment**: \~10-15 hours (spread over days/weeks).

***

### Part 1: Vite Basics

#### 1.1 What is Vite?

Vite is a **build tool and development server** that bundles JavaScript, CSS, and assets for web apps. It’s faster than Webpack due to native ES modules and esbuild.

* **Why Vite?**
  * Lightning-fast development server with Hot Module Replacement (HMR).
  * Simple configuration compared to Webpack.
  * Optimized production builds.
  * Used by modern frameworks like React, Vue, and Svelte.
* **Example**: A React app where Vite serves files instantly during development and creates a tiny production bundle.

#### 1.2 Creating a Vite Project

Vite sets up projects with a single command.

**Example**:

```bash
npm create vite@latest my-vite-app -- --template vanilla
cd my-vite-app
npm install
npm run dev
```

* Opens `http://localhost:5173`.
*   Creates:

    ```
    my-vite-app/
    ├── src/
    │   ├── main.js
    │   ├── style.css
    ├── index.html
    ├── vite.config.js
    ├── package.json
    ```

**Example (index.html)**:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Vite App</title>
  </head>
  <body>
    <div id="app"></div>
    <script type="module" src="/src/main.js"></script>
  </body>
</html>
```

```javascript
// src/main.js
import './style.css';

document.querySelector('#app').innerHTML = '<h1>Yo, Vite!</h1>';
```

```css
/* src/style.css */
h1 {
  color: blue;
}
```

**Exercise**:

1. Create a Vite project with the vanilla template.
2. Update `main.js` to show “Hello, Vite!” in a `<p>`.

**Answer**:

```javascript
// src/main.js
import './style.css';

document.querySelector('#app').innerHTML = '<p>Hello, Vite!</p>';
```

***

### Part 2: Vite with React

Set up Vite for a React app.

**Example**:

```bash
npm create vite@latest vite-react-app -- --template react
cd vite-react-app
npm install
npm run dev
```

```jsx
// src/main.jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';
import './index.css';

ReactDOM.createRoot(document.getElementById('root')).render(<App />);
```

```jsx
// src/App.jsx
import { useState } from 'react';

export default function App() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <h1>Yo, Vite + React!</h1>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

**Exercise**:

1. Create a React component `Greeting.jsx` that shows “Hello, \[name]!” with an input to update `name`.
2. Import it into `App.jsx`.

**Answer**:

```jsx
// src/Greeting.jsx
import { useState } from 'react';

export default function Greeting() {
  const [name, setName] = useState('');
  return (
    <div>
      <input
        value={name}
        onChange={(e) => setName(e.target.value)}
        placeholder="Your name"
      />
      <p>Hello, {name || 'stranger'}!</p>
    </div>
  );
}
```

```jsx
// src/App.jsx
import Greeting from './Greeting';

export default function App() {
  return (
    <div>
      <h1>Vite + React</h1>
      <Greeting />
    </div>
  );
}
```

***

### Part 3: Vite Configuration

Customize Vite with `vite.config.js`.

**Example**:

```javascript
// vite.config.js
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

export default defineConfig({
  plugins: [react()],
  server: {
    port: 3000,
  },
});
```

* `react()`: Enables React support.
* `port`: Sets dev server to `http://localhost:3000`.

**Exercise**:

1. Change the dev server port to 4000.
2. Add a base path `/my-app` for deployment.

**Answer**:

```javascript
// vite.config.js
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

export default defineConfig({
  plugins: [react()],
  server: {
    port: 4000,
  },
  base: '/my-app',
});
```

***

### Part 4: Advanced Vite Features

#### 4.1 Plugins

Vite plugins extend functionality (e.g., TypeScript, legacy browser support).

**Example (vite-plugin-svgr)**:

```bash
npm install vite-plugin-svgr --save-dev
```

```javascript
// vite.config.js
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';
import svgr from 'vite-plugin-svgr';

export default defineConfig({
  plugins: [react(), svgr()],
});
```

```jsx
// src/App.jsx
import Icon from './icon.svg?react';

export default function App() {
  return (
    <div>
      <h1>Vite + SVG</h1>
      <Icon />
    </div>
  );
}
```

**Exercise**:

1. Install `vite-plugin-svgr` and use an SVG as a React component.

#### 4.2 Code Splitting

Vite handles code splitting automatically with dynamic imports.

**Example**:

```jsx
// src/App.jsx
import { useState } from 'react';

export default function App() {
  const [Component, setComponent] = useState(null);

  const loadComponent = async () => {
    const { default: Dynamic } = await import('./Dynamic');
    setComponent(<Dynamic />);
  };

  return (
    <div>
      <button onClick={loadComponent}>Load</button>
      {Component}
    </div>
  );
}
```

```jsx
// src/Dynamic.jsx
export default function Dynamic() {
  return <p>Loaded dynamically!</p>;
}
```

**Exercise**:

1. Create a dynamic import for a `Message.jsx` component that shows “Yo!”.

***

### Part 5: Environment Variables

Use `.env` files for configuration.

**Example**:

```env
# .env
VITE_API_URL=https://api.example.com
```

```jsx
// src/App.jsx
export default function App() {
  return <p>API: {import.meta.env.VITE_API_URL}</p>;
}
```

**Exercise**:

1. Create a `.env` with `VITE_APP_TITLE` and display it in `App.jsx`.

**Answer**:

```env
# .env
VITE_APP_TITLE=My Vite App
```

```jsx
// src/App.jsx
export default function App() {
  return <h1>{import.meta.env.VITE_APP_TITLE}</h1>;
}
```

***

### Part 6: Project Setup

1. **Install Node.js**: [Download LTS](https://nodejs.org).
2.  **Create Project**:

    ```bash
    npm create vite@latest vite-react-app -- --template react
    cd vite-react-app
    npm install
    npm run dev
    ```
3. Open `http://localhost:5173`.

**Structure**:

```
vite-react-app/
├── src/
│   ├── main.jsx
│   ├── App.jsx
│   ├── index.css
├── public/
├── vite.config.js
├── package.json
```

***

### Part 7: Project: React To-Do List with Vite

**Goal**: Build a to-do list app with Vite, including localStorage.

**Code (src/App.jsx)**:

```jsx
import { useState, useEffect } from 'react';
import './App.css';

export default function App() {
  const [todos, setTodos] = useState(() => {
    const saved = localStorage.getItem('todos');
    return saved ? JSON.parse(saved) : [];
  });
  const [input, setInput] = useState('');

  useEffect(() => {
    localStorage.setItem('todos', JSON.stringify(todos));
  }, [todos]);

  const addTodo = () => {
    if (input.trim()) {
      setTodos([...todos, { id: Date.now(), text: input, done: false }]);
      setInput('');
    }
  };

  const toggleTodo = (id) => {
    setTodos(
      todos.map((todo) =>
        todo.id === id ? { ...todo, done: !todo.done } : todo
      )
    );
  };

  const deleteTodo = (id) => {
    setTodos(todos.filter((todo) => todo.id !== id));
  };

  return (
    <div className="todo-app">
      <h1>To-Do List</h1>
      <div className="input-container">
        <input
          value={input}
          onChange={(e) => setInput(e.target.value)}
          placeholder="Add a task"
          onKeyPress={(e) => e.key === 'Enter' && addTodo()}
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
              onClick={(e) => {
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
}
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

1. Set up the project (Part 6).
2. Replace `src/App.jsx` and `src/App.css` with the code above.
3. Run `npm run dev`.

**Exercises**:

1. Add a “Clear All” button.
2. Use an environment variable for the app title.
3. Add a filter for incomplete tasks.

**Answer (Clear All)**:

```jsx
const clearAll = () => setTodos([]);
// Add to JSX:
<button onClick={clearAll}>Clear All</button>
```

***

### Part 8: Pro Practices

#### 8.1 Optimization

* **Production Build**: Run `npm run build` to create `dist/`.
* **Tree Shaking**: Vite does this automatically.
* **Asset Handling**: Use `?url` for images (e.g., `import img from './img.png?url'`).

#### 8.2 Debugging

* Use Chrome DevTools with Vite’s source maps.
* Check console for errors.

#### 8.3 Deployment

* Build: `npm run build`.
* Deploy `dist/` to Vercel or Netlify.

***

### Part 9: Next Steps

1. **Advanced Vite**: Explore plugins like `vite-plugin-pwa` for PWAs.
2. **Integrations**: Use with TypeScript, Tailwind CSS.
3. **Performance**: Analyze bundles with `vite-plugin-bundle-analyzer`.
4. **Projects**: Build a portfolio or dashboard.

**Resources**:

* [Vite Docs](https://vitejs.dev)
* X’s #ViteJS tag for community tips

***

### Conclusion

You’ve mastered Vite: setup, React integration, plugins, and optimization. The to-do list project applies these skills. Keep practicing by extending the project or building new apps. Search X for #ViteJS if you’re stuck, or ask me for help!
