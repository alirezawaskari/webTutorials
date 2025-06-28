---
description: From Zero to Expert
---

# Next.js Pro Course

### Introduction

This course is for beginners with HTML, CSS, basic JavaScript (variables, functions, arrays), and some React knowledge (components, props, state, hooks). You’ll learn **Next.js**, a powerful React framework for building fast, SEO-friendly, production-ready web apps. By the end, you’ll master Next.js core and advanced features, build three projects (a to-do list, a blog, and a mini e-commerce site), and be ready to create professional apps or land a job. This is a hands-on, no-BS guide to make you a Next.js pro.

**What You’ll Learn**:

1. Next.js basics (pages, routing, JSX, React integration).
2. Static Site Generation (SSG) and Server-Side Rendering (SSR).
3. API routes for backend functionality.
4. State management and data fetching.
5. Styling and optimization.
6. Deployment and real-world practices.
7. Projects: To-do list, blog, and mini e-commerce site.

**Tools Needed**:

* **Node.js**: [Download LTS](https://nodejs.org) (installs `npm`).
* **VS Code**: [Free download](https://code.visualstudio.com/).
* A browser (Chrome recommended).
* Optional: [Postman](https://www.postman.com/) for testing API routes.

**How to Use This Document**:

* Save as `NextJS_Pro_Course.md` or convert to PDF (e.g., VS Code with “Markdown PDF” extension).
* Follow each section, code the examples, and do the exercises.
* Set up a Next.js project (Part 7) to code along.
* Build the projects in Part 8 to apply your skills.
* Refer to resources for extra learning.

**Time Commitment**: \~20-30 hours (spread over days/weeks).

***

### Part 1: Next.js Basics

#### 1.1 What is Next.js?

Next.js is a **React framework** that simplifies building web apps with features like server-side rendering (SSR), static site generation (SSG), file-based routing, and built-in API routes.

* **Why Next.js?**
  * Enhances React with SEO-friendly rendering (SSR/SSG).
  * Simplifies routing (no need for `react-router-dom`).
  * Built-in API routes for backend logic.
  * Used by Netflix, TikTok, and Hulu for fast, scalable apps.
* **Example**: A blog where pages load instantly (SSG) and data is fetched server-side (SSR).

#### 1.2 Pages and File-Based Routing

Next.js uses a file-based routing system. Files in the `pages/` folder become routes.

**Example**:

```
pages/
├── index.js      // Route: /
├── about.js      // Route: /about
```

```jsx
// pages/index.js
export default function Home() {
  return <h1>Yo, Welcome to Next.js!</h1>;
}

// pages/about.js
export default function About() {
  return <h1>About Page</h1>;
}
```

* Visit `http://localhost:3000` for `index.js`, `/about` for `about.js`.

**Exercise**:

1. Create a `contact.js` page that shows “Contact Us” in an `<h1>`.
2. What’s the URL for `contact.js`?

**Answer**:

```jsx
// pages/contact.js
export default function Contact() {
  return <h1>Contact Us</h1>;
}
// URL: /contact
```

#### 1.3 React in Next.js

Next.js uses React components. You can use props, state, and hooks just like in React.

**Example**:

```jsx
// pages/index.js
import { useState } from 'react';

export default function Counter() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

**Exercise**:

1. Create a page `greeting.js` with a state variable `name` and an input to update it.

**Answer**:

```jsx
// pages/greeting.js
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
      <p>Yo, {name || 'stranger'}!</p>
    </div>
  );
}
```

***

### Part 2: Static Site Generation (SSG) and Server-Side Rendering (SSR)

#### 2.1 Static Site Generation (SSG)

SSG pre-renders pages at build time, making them fast and SEO-friendly.

**Use `getStaticProps`**:

```jsx
// pages/posts.js
export default function Posts({ posts }) {
  return (
    <ul>
      {posts.map((post) => (
        <li key={post.id}>{post.title}</li>
      ))}
    </ul>
  );
}

export async function getStaticProps() {
  const res = await fetch('https://jsonplaceholder.typicode.com/posts');
  const posts = await res.json();
  return { props: { posts } };
}
```

* `getStaticProps` fetches data at build time.
* Data is passed as props to the page.

**Exercise**:

1. Create a `users.js` page that fetches and displays user names from `https://jsonplaceholder.typicode.com/users`.

**Answer**:

```jsx
// pages/users.js
export default function Users({ users }) {
  return (
    <ul>
      {users.map((user) => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}

export async function getStaticProps() {
  const res = await fetch('https://jsonplaceholder.typicode.com/users');
 umar
  const users = await res.json();
  return { props: { users } };
}
```

#### 2.2 Server-Side Rendering (SSR)

SSR renders pages on each request, ideal for dynamic data.

**Use `getServerSideProps`**:

```jsx
// pages/news.js
export default function News({ articles }) {
  return (
    <ul>
      {articles.map((article) => (
        <li key={article.id}>{article.title}</li>
      ))}
    </ul>
  );
}

export async function getServerSideProps() {
  const res = await fetch('https://jsonplaceholder.typicode.com/posts');
  const articles = await res.json();
  return { props: { articles } };
}
```

**Exercise**:

1. Create a `todos.js` page with SSR to fetch todos from `https://jsonplaceholder.typicode.com/todos`.

**Answer**:

```jsx
// pages/todos.js
export default function Todos({ todos }) {
  return (
    <ul>
      {todos.map((todo) => (
        <li key={todo.id}>{todo.title}</li>
      ))}
    </ul>
  );
}

export async function getServerSideProps() {
  const res = await fetch('https://jsonplaceholder.typicode.com/todos');
  const todos = await res.json();
  return { props: { todos } };
}
```

***

### Part 3: Dynamic Routes

Create dynamic routes with file names like `[id].js`.

**Example**:

```jsx
// pages/posts/[id].js
export default function Post({ post }) {
  return (
    <div>
      <h1>{post.title}</h1>
      <p>{post.body}</p>
    </div>
  );
}

export async function getStaticProps({ params }) {
  const res = await fetch(`https://jsonplaceholder.typicode.com/posts/${params.id}`);
  const post = await res.json();
  return { props: { post } };
}

export async function getStaticPaths() {
  const res = await fetch('https://jsonplaceholder.typicode.com/posts');
  const posts = await res.json();
  const paths = posts.map((post) => ({ params: { id: post.id.toString() } }));
  return { paths, fallback: false };
}
```

* `[id].js` creates routes like `/posts/1`, `/posts/2`.
* `getStaticPaths` defines valid IDs.

**Exercise**:

1. Create a dynamic route `pages/users/[id].js` to show user details.

***

### Part 4: API Routes

Next.js lets you create backend API routes in `pages/api/`.

**Example**:

```jsx
// pages/api/hello.js
export default function handler(req, res) {
  res.status(200).json({ message: 'Yo, Dude!' });
}
```

* Access at `/api/hello`.

**Example with Data**:

```jsx
// pages/api/todos.js
export default function handler(req, res) {
  const todos = [{ id: 1, text: 'Learn Next.js' }];
  res.status(200).json(todos);
}
```

**Exercise**:

1. Create an API route `pages/api/users.js` that returns a list of users.

**Answer**:

```jsx
// pages/api/users.js
export default function handler(req, res) {
  const users = [{ id: 1, name: 'Dude' }, { id: 2, name: 'Alice' }];
  res.status(200).json(users);
}
```

***

### Part 5: State Management

Use React’s `useState`, `useReducer`, or `useContext` for small apps. For large apps, use **Redux Toolkit**.

**Example (Redux)**:

```jsx
// lib/store.js
import { configureStore } from '@reduxjs/toolkit';
import { createSlice } from '@reduxjs/toolkit';

const counterSlice = createSlice({
  name: 'counter',
  initialState: { count: 0 },
  reducers: {
    increment: (state) => { state.count += 1; },
    decrement: (state) => { state.count -= 1; },
  },
});

export const { increment, decrement } = counterSlice.actions;
export const store = configureStore({ reducer: counterSlice.reducer });

// pages/_app.js
import { Provider } from 'react-redux';
import { store } from '../lib/store';

export default function MyApp({ Component, pageProps }) {
  return (
    <Provider store={store}>
      <Component {...pageProps} />
    </Provider>
  );
}

// pages/index.js
import { useSelector, useDispatch } from 'react-redux';
import { increment, decrement } from '../lib/store';

export default function Home() {
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
```

**Exercise**:

1. Create a Redux slice for a `theme` (light/dark) and toggle it.

***

### Part 6: Styling

Use CSS modules, Tailwind CSS, or inline styles.

**CSS Modules**:

```jsx
// components/Card.js
import styles from './Card.module.css';

export default function Card() {
  return <div className={styles.card}>Styled Card</div>;
}
```

```css
/* components/Card.module.css */
.card {
  border: 1px solid #ccc;
  padding: 15px;
  border-radius: 5px;
}
```

**Tailwind (requires setup)**:

```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

```jsx
// pages/index.js
export default function Home() {
  return <div className="border border-gray-300 p-4 rounded-md">Styled</div>;
}
```

**Exercise**:

1. Style a component with CSS modules to have a border and padding.

***

### Part 7: Project Setup

1. **Install Node.js**: [Download LTS](https://nodejs.org).
2.  **Create Project**:

    ```bash
    npx create-next-app@latest next-pro-app
    cd next-pro-app
    npm install @reduxjs/toolkit react-redux axios
    npm run dev
    ```
3. Open `http://localhost:3000`.

**Structure**:

```
next-pro-app/
├── pages/
│   ├── api/
│   ├── _app.js
│   ├── index.js
├── styles/
├── components/
├── lib/
├── package.json
```

***

### Part 8: Projects

#### Project 1: To-Do List

**Goal**: Add, toggle, and delete tasks with localStorage and SSR.

**Code (pages/todos.js)**:

```jsx
import { useState, useEffect } from 'react';
import styles from '../styles/Todos.module.css';

export default function Todos({ initialTodos }) {
  const [todos, setTodos] = useState(initialTodos);
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
    <div className={styles.container}>
      <h1>To-Do List</h1>
      <div className={styles.inputContainer}>
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
            className={todo.done ? styles.done : ''}
            onClick={() => toggleTodo(todo.id)}
          >
            {todo.text}
            <button
              className={styles.deleteBtn}
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

export async function getServerSideProps() {
  const initialTodos = JSON.parse(localStorage.getItem('todos') || '[]');
  return { props: { initialTodos } };
}
```

**CSS (styles/Todos.module.css)**:

```css
.container {
  max-width: 500px;
  margin: 20px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.inputContainer {
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
  flatpak install flathub com.visualstudio.code
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

.deleteBtn {
  background-color: #dc3545;
}

.deleteBtn:hover {
  background-color: #c82333;
}
```

**Exercises**:

1. Add a “Clear All” button.
2. Create an API route `/api/todos` to fetch todos.

#### Project 2: Blog with SSG

**Goal**: Display blog posts fetched at build time.

**Code (pages/blog/index.js)**:

```jsx
import Link from 'next/link';
import styles from '../../styles/Blog.module.css';

export default function Blog({ posts }) {
  return (
    <div className={styles.container}>
      <h1>Blog</h1>
      <ul>
        {posts.map((post) => (
          <li key={post.id}>
            <Link href={`/blog/${post.id}`}>{post.title}</Link>
          </li>
        ))}
      </ul>
    </div>
  );
}

export async function getStaticProps() {
  const res = await fetch('https://jsonplaceholder.typicode.com/posts');
  const posts = await res.json();
  return { props: { posts } };
}
```

**Code (pages/blog/\[id].js)**:

```jsx
import styles from '../../styles/Blog.module.css';

export default function Post({ post }) {
  return (
    <div className={styles.container}>
      <h1>{post.title}</h1>
      <p>{post.body}</p>
    </div>
  );
}

export async function getStaticProps({ params }) {
  const res = await fetch(`https://jsonplaceholder.typicode.com/posts/${params.id}`);
  const post = await res.json();
  return { props: { post } };
}

export async function getStaticPaths() {
  const res = await fetch('https://jsonplaceholder.typicode.com/posts');
  const posts = await res.json();
  const paths = posts.map((post) => ({ params: { id: post.id.toString() } }));
  return { paths, fallback: false };
}
```

**CSS (styles/Blog.module.css)**:

```css
.container {
  max-width: 600px;
  margin: 20px auto;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  margin: 10px 0;
}

a {
  color: #007bff;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}
```

**Exercises**:

1. Add a “Back to Blog” link on the post page.
2. Style posts with a card layout.

#### Project 3: Mini E-Commerce Site

**Goal**: Display products, add to cart, and use an API route.

**Code (pages/shop/index.js)**:

```jsx
import { useState } from 'react';
import Link from 'next/link';
import styles from '../../styles/Shop.module.css';

export default function Shop({ products }) {
  const [cart, setCart] = useState([]);

  const addToCart = (product) => {
    setCart([...cart, product]);
  };

  return (
    <div className={styles.container}>
      <h1>Shop</h1>
      <h2>Products</h2>
      <ul>
        {products.map((product) => (
          <li key={product.id}>
            <Link href={`/shop/${product.id}`}>{product.name}</Link> - ${product.price}
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

export async function getStaticProps() {
  const products = [
    { id: 1, name: 'Laptop', price: 999 },
    { id: 2, name: 'Phone', price: 499 },
  ];
  return { props: { products } };
}
```

**Code (pages/shop/\[id].js)**:

```jsx
import styles from '../../styles/Shop.module.css';

export default function Product({ product }) {
  return (
    <div className={styles.container}>
      <h1>{product.name}</h1>
      <p>Price: ${product.price}</p>
    </div>
  );
}

export async function getStaticProps({ params }) {
  const products = [
    { id: 1, name: 'Laptop', price: 999 },
    { id: 2, name: 'Phone', price: 499 },
  ];
  const product = products.find((p) => p.id === parseInt(params.id));
  return { props: { product } };
}

export async function getStaticPaths() {
  const products = [
    { id: 1, name: 'Laptop', price: 999 },
    { id: 2, name: 'Phone', price: 499 },
  ];
  const paths = products.map((p) => ({ params: { id: p.id.toString() } }));
  return { paths, fallback: false };
}
```

**CSS (styles/Shop.module.css)**:

```css
.container {
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

a {
  color: #007bff;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}
```

**Exercises**:

1. Create an API route `/api/cart` to manage cart items.
2. Add a “Remove from Cart” button.

***

### Part 9: Pro Practices

#### 9.1 Folder Structure

```
next-pro-app/
├── pages/
│   ├── api/
│   ├── _app.js
│   ├── index.js
├── components/
├── styles/
├── lib/
├── public/
├── package.json
```

#### 9.2 Debugging

* Use Chrome DevTools with Next.js extension.
* Log props/state with `console.log`.
* Check `/api` routes with Postman.

#### 9.3 Testing

Use Jest and React Testing Library:

```jsx
import { render, screen } from '@testing-library/react';
import Todos from '../pages/todos';

test('renders to-do list', () => {
  render(<Todos initialTodos={[]} />);
  expect(screen.getByText('To-Do List')).toBeInTheDocument();
});
```

#### 9.4 TypeScript

Add TypeScript:

```jsx
// pages/index.tsx
interface Props {
  message: string;
}

export default function Home({ message }: Props) {
  return <h1>{message}</h1>;
}

export async function getStaticProps() {
  return { props: { message: 'Yo, Dude!' } };
}
```

#### 9.5 Deployment

Deploy to **Vercel**:

```bash
npm run build
vercel
```

***

### Part 10: Next Steps

1. **Advanced Next.js**: Learn Incremental Static Regeneration (ISR), middleware.
2. **Backend**: Integrate with MongoDB or Supabase.
3. **Authentication**: Use NextAuth.js for login systems.
4. **Portfolio**: Build a personal site with Next.js.
5. **Contribute**: Explore open-source Next.js projects on GitHub.

**Resources**:

* [Next.js Docs](https://nextjs.org/docs)
* [Vercel Tutorials](https://vercel.com/guides)
* X’s #NextJS tag for community tips

***

### Conclusion

You’ve mastered Next.js: pages, routing, SSG, SSR, API routes, state management, and more. The three projects (to-do list, blog, e-commerce) prepare you for real-world apps. Keep practicing by extending these projects or building new ones. Search X for #NextJS if you’re stuck, or ask me for help!
