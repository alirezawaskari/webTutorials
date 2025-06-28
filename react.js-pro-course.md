---
description: From Zero to Expert
---

# React.js Pro Course

### Introduction

This course is for beginners with HTML, CSS, and basic JavaScript knowledge (variables, functions, arrays, maybe DOM manipulation). You’ll learn **React.js**, a JavaScript library for building dynamic, interactive web interfaces, from scratch to pro level. By the end, you’ll master React’s core and advanced concepts, build multiple projects (a to-do list, a movie search app, and a mini e-commerce site), and be ready to tackle real-world apps or land a job. This is a hands-on, no-BS guide designed to make you a React expert.

**What You’ll Learn**:

1. Core React: Components, JSX, props, state, events.
2. Advanced React: Hooks (useState, useEffect, useReducer, useContext), custom hooks, performance optimization.
3. Real-World Skills: Routing, state management (Redux), API integration, testing, TypeScript basics.
4. Projects: To-do list, movie search app, and a mini e-commerce site.
5. Pro Practices: Folder structure, debugging, deployment.

**Tools Needed**:

* **Node.js**: [Download LTS](https://nodejs.org) (installs `npm`).
* **VS Code**: [Free download](https://code.visualstudio.com/).
* A browser (Chrome recommended).
* Optional: [Postman](https://www.postman.com/) for testing APIs.

**How to Use This Document**:

* Save as `React_Pro_Course.md` or convert to PDF (e.g., VS Code with “Markdown PDF” extension).
* Follow each section, code the examples, and do the exercises.
* Set up a React project (Part 7) to code along.
* Build the projects in Part 8 to apply your skills.
* Refer to resources for extra learning.

**Time Commitment**: \~20-30 hours (spread over days/weeks, depending on pace).

***

### Part 1: React Core Concepts

#### 1.1 What is React?

React is a **JavaScript library** for building interactive user interfaces. It’s used by companies like Facebook, Netflix, and Airbnb for fast, dynamic websites.

* **Key Features**:
  * **Components**: Reusable UI pieces (e.g., buttons, forms).
  * **Virtual DOM**: Updates only changed parts of the UI for speed.
  * **Declarative**: Describe _what_ the UI should look like, not _how_ to update it.
* **Why Learn It?**
  * Simplifies complex UI logic compared to vanilla JavaScript.
  * Huge job demand (React devs earn $80k-$120k+ in many markets).
  * Scales from small to large apps.

**Example**: A Twitter-like app where each tweet is a component that updates when liked.

#### 1.2 Components and JSX

**Components** are functions (or classes) that return UI. Functional components are the modern standard.

**JSX** is a syntax for writing HTML-like code in JavaScript. It’s transpiled to JavaScript by tools like Vite.

**Example**:

```jsx
function Welcome() {
  const name = "Dude";
  return <h1>Yo, {name}!</h1>;
}
```

* Use it: `<Welcome />` (renders “Yo, Dude!”).
* **JSX Rules**:
  * One root element (use `<div>` or `<>...</>` fragment).
  * `className` instead of `class`.
  * JavaScript in `{}` (e.g., `{2 + 2}` renders `4`).

**Exercise**:

1. Write a `Header` component that returns an `<h1>` with “My React App”.
2. Create a `Profile` component that shows a `<p>` with “Name: \[your name]”.

**Answers**:

```jsx
function Header() {
  return <h1>My React App</h1>;
}

function Profile() {
  return <p>Name: Dude</p>;
}
```

#### 1.3 Props (Passing Data)

**Props** let you pass data to components, making them reusable.

**Example**:

```jsx
function Welcome(props) {
  return <h1>Yo, {props.name}!</h1>;
}
```

* Use: `<Welcome name="Dude" />`.

**Multiple Props**:

```jsx
function UserCard(props) {
  return (
    <div>
      <h2>{props.name}</h2>
      <p>Age: {props.age}</p>
    </div>
  );
}
```

* Use: `<UserCard name="Alice" age={25} />`.

**Exercise**:

1. Create a `Product` component that takes `title` and `price` props and shows them in a `<div>`.
2. Use it with `title="Laptop"` and `price={999}`.

**Answer**:

```jsx
function Product(props) {
  return (
    <div>
      <h3>{props.title}</h3>
      <p>Price: ${props.price}</p>
    </div>
  );
}
// Use: <Product title="Laptop" price={999} />
```

***

### Part 2: State and Interactivity

#### 2.1 State (Dynamic Data)

**State** is data that changes (e.g., form inputs, counters). Use the `useState` hook.

**Example**:

```jsx
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

* `useState(0)`: `count` is the state, `setCount` updates it.
* Clicking updates `count`, and React re-renders.

**Rule**: Use `setCount`, not `count = count + 1`.

**Exercise**:

1. Create a component with a `score` state starting at 100. Add buttons to add or subtract 10.
2. Why is `count = count + 1` wrong?

**Answer**:

```jsx
import { useState } from 'react';

function ScoreBoard() {
  const [score, setScore] = useState(100);
  return (
    <div>
      <p>Score: {score}</p>
      <button onClick={() => setScore(score + 10)}>+10</button>
      <button onClick={() => setScore(score - 10)}>-10</button>
    </div>
  );
}
```

* Wrong: `count = count + 1` doesn’t trigger re-render.

#### 2.2 Event Handling

Handle user actions with camelCase events (e.g., `onClick`, `onChange`).

**Example (Click)**:

```jsx
function Button() {
  const handleClick = () => alert('Clicked!');
  return <button onClick={handleClick}>Click Me</button>;
}
```

**Example (Form)**:

```jsx
import { useState } from 'react';

function NameInput() {
  const [name, setName] = useState('');
  return (
    <div>
      <input
        value={name}
        onChange={(e) => setName(e.target.value)}
        placeholder="Type your name"
      />
      <p>Hello, {name || 'stranger'}!</p>
    </div>
  );
}
```

**Exercise**:

1. Create a component with a button that sets a `message` state to “Hello!”.
2. Make an input that updates a `city` state as you type.

**Answer**:

```jsx
import { useState } from 'react';

function MessageButton() {
  const [message, setMessage] = useState('');
  return (
    <div>
      <p>{message}</p>
      <button onClick={() => setMessage('Hello!')}>Say Hello</button>
    </div>
  );
}

function CityInput() {
  const [city, setCity] = useState('');
  return (
    <div>
      <input
        value={city}
        onChange={(e) => setCity(e.target.value)}
        placeholder="Enter city"
      />
      <p>City: {city}</p>
    </div>
  );
}
```

***

### Part 3: Lists and Conditional Rendering

#### 3.1 Rendering Lists

Use `map` to render arrays. Each item needs a unique `key`.

**Example**:

```jsx
function TodoList() {
  const todos = ['Learn React', 'Build App', 'Party'];
  return (
    <ul>
      {todos.map((todo) => (
        <li key={todo}>{todo}</li>
      ))}
    </ul>
  );
}
```

**Exercise**:

1. Render an array `books = ['React 101', 'JS Pro']` as `<p>` tags.
2. Why do keys matter?

**Answer**:

```jsx
function BookList() {
  const books = ['React 101', 'JS Pro'];
  return (
    <div>
      {books.map((book) => (
        <p key={book}>{book}</p>
      ))}
    </div>
  );
}
```

* Keys help React update lists efficiently.

#### 3.2 Conditional Rendering

Show/hide UI with `if`, `&&`, or ternaries.

**Example**:

```jsx
function LoginStatus({ isLoggedIn }) {
  return (
    <div>
      {isLoggedIn ? <p>Welcome!</p> : <p>Log in!</p>}
    </div>
  );
}
```

**Exercise**:

1. Show “Winner!” if a `score` state is 100 or more, else “Keep going!”.
2. Use `&&` to show a `<p>Alert!</p>` if a prop `showAlert` is true.

**Answer**:

```jsx
import { useState } from 'react';

function GameStatus() {
  const [score, setScore] = useState(50);
  return (
    <div>
      <p>{score >= 100 ? 'Winner!' : 'Keep going!'}</p>
      <button onClick={() => setScore(score + 50)}>Add 50</button>
    </div>
  );
}

function Alert({ showAlert }) {
  return <div>{showAlert && <p>Alert!</p>}</div>;
}
```

***

### Part 4: Hooks

#### 4.1 useState

Covered in Part 2.1.

#### 4.2 useEffect

Runs side effects (e.g., fetching data, timers) after rendering.

**Example**:

```jsx
import { useState, useEffect } from 'react';

function DataFetcher() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/todos/1')
      .then((res) => res.json())
      .then((data) => setData(data.title));
  }, []);

  return <div>{data || 'Loading...'}</div>;
}
```

**Exercise**:

1. Create a `useEffect` that logs “Loaded!” on mount.
2. Add a `useEffect` that updates a `time` state every second.

**Answer**:

```jsx
import { useState, useEffect } from 'react';

function Logger() {
  useEffect(() => {
    console.log('Loaded!');
  }, []);
  return <p>Check console!</p>;
}

function Timer() {
  const [time, setTime] = useState(0);
  useEffect(() => {
    const interval = setInterval(() => setTime((t) => t + 1), 1000);
    return () => clearInterval(interval); // Cleanup
  }, []);
  return <p>Seconds: {time}</p>;
}
```

#### 4.3 useContext

Shares data across components.

**Example**:

```jsx
import { createContext, useContext } from 'react';

const ThemeContext = createContext('light');

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <ThemedButton />
    </ThemeContext.Provider>
  );
}

function ThemedButton() {
  const theme = useContext(ThemeContext);
  return (
    <button style={{ background: theme === 'dark' ? '#333' : '#fff', color: theme === 'dark' ? '#fff' : '#000' }}>
      Themed
    </button>
  );
}
```

**Exercise**:

1. Create a `UserContext` with a `name` and use it to show “Hi, \[name]!”.

**Answer**:

```jsx
import { createContext, useContext } from 'react';

const UserContext = createContext({ name: 'Guest' });

function App() {
  return (
    <UserContext.Provider value={{ name: 'Dude' }}>
      <UserGreeting />
    </UserContext.Provider>
  );
}

function UserGreeting() {
  const user = useContext(UserContext);
  return <p>Hi, {user.name}!</p>;
}
```

#### 4.4 useReducer

Manages complex state logic.

**Example**:

```jsx
import { useReducer } from 'react';

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, { count: 0 });
  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
    </div>
  );
}
```

**Exercise**:

1. Create a `useReducer` for a todo list with `add` and `clear` actions.

***

### Part 5: Routing

Use `react-router-dom` for multi-page apps.

**Example**:

```jsx
import { BrowserRouter, Route, Routes, Link } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link> | <Link to="/about">About</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}

function Home() { return <h1>Home</h1>; }
function About() { return <h1>About</h1>; }
```

**Exercise**:

1. Add routes for `/profile` and `/settings`.

**Answer**:

```jsx
import { BrowserRouter, Route, Routes, Link } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/profile">Profile</Link> | <Link to="/settings">Settings</Link>
      </nav>
      <Routes>
        <Route path="/profile" element={<Profile />} />
        <Route path="/settings" element={<Settings />} />
      </Routes>
    </BrowserRouter>
  );
}

function Profile() { return <h1>Profile</h1>; }
function Settings() { return <h1>Settings</h1>; }
```

***

### Part 6: State Management (Redux)

For large apps, use **Redux** to manage global state.

**Setup**:

```bash
npm install @reduxjs/toolkit react-redux
```

**Example**:

```jsx
import { configureStore } from '@reduxjs/toolkit';
import { Provider, useSelector, useDispatch } from 'react-redux';
import { createSlice } from '@reduxjs/toolkit';

// Redux slice
const counterSlice = createSlice({
  name: 'counter',
  initialState: { count: 0 },
  reducers: {
    increment: (state) => { state.count += 1; },
    decrement: (state) => { state.count -= 1; },
  },
});

const store = configureStore({ reducer: counterSlice.reducer });
const { increment, decrement } = counterSlice.actions;

function Counter() {
  const count = useSelector((state) => state.count);
  const dispatch = useDispatch();
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => dispatch(increment())}>+</button>
      <button onClick={() => dispatch(decrement())}>-</button>
    </div>
  );
}

function App() {
  return (
    <Provider store={store}>
      <Counter />
    </Provider>
  );
}
```

**Exercise**:

1. Create a Redux slice for a `theme` (light/dark) and toggle it.

***

### Part 7: Styling

Use CSS, inline styles, or Tailwind CSS.

**CSS Example**:

```css
/* src/App.css */
.card {
  border: 1px solid #ccc;
  padding: 15px;
  margin: 10px;
  border-radius: 5px;
}
```

```jsx
function Card() {
  return <div className="card">Styled Card</div>;
}
```

**Tailwind Example** (requires setup):

```jsx
function Card() {
  return <div className="border border-gray-300 p-4 rounded-md">Styled Card</div>;
}
```

**Exercise**:

1. Style a `<div>` with a border, padding, and background color.

***

### Part 8: Project Setup

1. **Install Node.js**: [Download LTS](https://nodejs.org).
2.  **Create Project**:

    ```bash
    npm create vite@latest react-pro-app -- --template react
    cd react-pro-app
    npm install
    npm install react-router-dom @reduxjs/toolkit react-redux
    npm run dev
    ```
3. Open `http://localhost:5173`.

**Structure**:

```
react-pro-app/
├── src/
│   ├── components/
│   ├── pages/
│   ├── App.jsx
│   ├── main.jsx
│   ├── index.css
├── package.json
```

***

### Part 9: Projects

#### Project 1: To-Do List

**Goal**: Add, toggle, and delete tasks with localStorage.

**Code (src/components/TodoApp.jsx)**:

```jsx
import { useState, useEffect } from 'react';
import './TodoApp.css';

function TodoApp() {
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

export default TodoApp;
```

**CSS (src/components/TodoApp.css)**:

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

li.done {
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

**Update src/App.jsx**:

```jsx
import TodoApp from './components/TodoApp';

function App() {
  return (
    <div>
      <TodoApp />
    </div>
  );
}

export default App;
```

**Exercises**:

1. Add a “Clear All” button.
2. Add a filter for incomplete tasks.
3. Add a task counter.

#### Project 2: Movie Search App

**Goal**: Search movies using an API (e.g., OMDB API).

**Setup**:

* Get a free API key from [OMDB](http://www.omdbapi.com/).
*   Install `axios`:

    ```bash
    npm install axios
    ```

**Code (src/components/MovieSearch.jsx)**:

```jsx
import { useState, useEffect } from 'react';
import axios from 'axios';
import './MovieSearch.css';

function MovieSearch() {
  const [query, setQuery] = useState('');
  const [movies, setMovies] = useState([]);
  const [loading, setLoading] = useState(false);

  useEffect(() => {
    if (!query) return;
    setLoading(true);
    axios
      .get(`http://www.omdbapi.com/?s=${query}&apikey=YOUR_API_KEY`)
      .then((res) => {
        setMovies(res.data.Search || []);
        setLoading(false);
      })
      .catch(() => setLoading(false));
  }, [query]);

  return (
    <div className="movie-search">
      <h1>Movie Search</h1>
      <input
        value={query}
        onChange={(e) => setQuery(e.target.value)}
        placeholder="Search movies..."
      />
      {loading && <p>Loading...</p>}
      <ul>
        {movies.map((movie) => (
          <li key={movie.imdbID}>
            <h3>{movie.Title}</h3>
            <p>{movie.Year}</p>
            <img src={movie.Poster} alt={movie.Title} />
          </li>
        ))}
      </ul>
    </div>
  );
}

export default MovieSearch;
```

**CSS (src/components/MovieSearch.css)**:

```css
.movie-search {
  max-width: 600px;
  margin: 20px auto;
}

input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  margin-bottom: 20px;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  margin: 10px 0;
}

img {
  max-width: 100px;
}
```

**Exercises**:

1. Add error handling for failed API calls.
2. Add a “Details” button to fetch more movie info.

#### Project 3: Mini E-Commerce Site

**Goal**: Display products, add to cart, and view cart.

**Code (src/components/Shop.jsx)**:

```jsx
import { useState } from 'react';
import './Shop.css';

function Shop() {
  const [products] = useState([
    { id: 1, name: 'Laptop', price: 999 },
    { id: 2, name: 'Phone', price: 499 },
  ]);
  const [cart, setCart] = useState([]);

  const addToCart = (product) => {
    setCart([...cart, product]);
  };

  return (
    <div className="shop">
      <h1>Shop</h1>
      <h2>Products</h2>
      <ul>
        {products.map((product) => (
          <li key={product.id}>
            <span>{product.name} - ${product.price}</span>
            <button onClick={() => addToCart(product)}>Add to Cart</button>
          </li>
        ))}
      </ul>
      <h2>Cart ({cart.length})</h2>
      <ul>
        {cart.map((item, index) => (
          <li key={index}>{item.name} - ${item.price}</li>
        ))}
      </ul>
    </div>
  );
}

export default Shop;
```

**CSS (src/components/Shop.css)**:

```css
.shop {
  max-width: 600px;
  margin: 20px auto;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  padding: 10px;
  border-bottom: 1px solid #eee;
}

button {
  background-color: #28a745;
  color: white;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
}

button:hover {
  background-color: #218838;
}
```

**Exercises**:

1. Add a “Remove from Cart” button.
2. Calculate the cart total.
3. Persist cart in localStorage.

***

### Part 10: Pro Practices

#### 10.1 Folder Structure

```
src/
├── components/    # Reusable components (e.g., Button, TodoApp)
├── pages/        # Page components (e.g., Home, About)
├── hooks/        # Custom hooks
├── context/      # Context files
├── redux/        # Redux slices, store
├── App.jsx
├── main.jsx
├── index.css
```

#### 10.2 Debugging

* Use Chrome DevTools (React Developer Tools extension).
* Log state/props with `console.log`.
* Check for errors in the console.

#### 10.3 Testing

Use **Jest** and **React Testing Library**:

```jsx
import { render, screen } from '@testing-library/react';
import TodoApp from './components/TodoApp';

test('renders to-do list', () => {
  render(<TodoApp />);
  expect(screen.getByText('To-Do List')).toBeInTheDocument();
});
```

#### 10.4 TypeScript Basics

Add TypeScript for type safety:

```jsx
interface Props {
  name: string;
  age: number;
}

function UserCard({ name, age }: Props) {
  return (
    <div>
      <h2>{name}</h2>
      <p>Age: {age}</p>
    </div>
  );
}
```

#### 10.5 Deployment

Deploy to **Vercel** or **Netlify**:

```bash
npm run build
# Follow Vercel/Netlify CLI instructions
```

***

### Part 11: Next Steps

1. **Advanced Hooks**: Learn `useMemo`, `useCallback`, custom hooks.
2. **Next.js**: For server-side rendering and SEO.
3. **GraphQL**: Use with Apollo for advanced APIs.
4. **Portfolio**: Build a personal site showcasing your projects.
5. **Contribute**: Explore open-source React projects on GitHub.

**Resources**:

* [React Docs](https://react.dev)
* [Redux Docs](https://redux.js.org)
* FreeCodeCamp React Course
* X’s #ReactJS tag for community tips

***

### Conclusion

You’ve learned React from core concepts (components, state, hooks) to advanced topics (Redux, TypeScript, routing). The three projects (to-do list, movie search, e-commerce) give you hands-on experience. Keep practicing by tweaking these or building new apps. Search X for #ReactJS or ask me for help if you’re stuck!
