---
description: From Zero to Expert
---

# Nuxt.js Pro Course

### Introduction

This course is for beginners with HTML, CSS, basic JavaScript (variables, functions, arrays), some React knowledge, and basic Vue.js knowledge (components, directives, Vuex). You’ll learn **Nuxt.js**, a Vue.js framework for building server-side rendered (SSR), static, or single-page applications (SPAs). Nuxt simplifies Vue development with file-based routing, automatic code splitting, and server-side features. By the end, you’ll master Nuxt’s core and advanced features, integrate it with Vite and TypeScript, and build a project to solidify your skills. This is a hands-on, no-BS guide to make you a Nuxt.js pro.

**What You’ll Learn**:

1. Nuxt.js basics (pages, layouts, routing).
2. Static Site Generation (SSG) and Server-Side Rendering (SSR).
3. Advanced features (Nuxt modules, Vuex, async data).
4. Integration with Vite and TypeScript.
5. Project: A Nuxt.js blog with SSG and SSR.

**Tools Needed**:

* **Node.js**: [Download LTS](https://nodejs.org) (installs `npm`).
* **VS Code**: [Free download](https://code.visualstudio.com/) with [Volar extension](https://marketplace.visualstudio.com/items?itemName=Vue.volar).
* A browser (Chrome recommended).

**How to Use This Document**:

* Save as `Nuxt_Pro_Course.md` or convert to PDF (e.g., VS Code with “Markdown PDF” extension).
* Follow each section, code the examples, and do the exercises.
* Set up a project (Part 5) to code along.
* Build the project in Part 6 to apply your skills.
* Refer to resources for extra learning.

**Time Commitment**: \~15-20 hours (spread over days/weeks).

***

### Part 1: Nuxt.js Basics

#### 1.1 What is Nuxt.js?

Nuxt.js is a **Vue.js framework** that enhances Vue with features like file-based routing, SSR, SSG, and automatic code splitting. It’s ideal for SEO-friendly apps and simplifies Vue development.

* **Why Nuxt.js?**
  * Automatic routing based on file structure (no Vue Router setup needed).
  * Supports SSR, SSG, and SPA modes.
  * Built-in Vuex and middleware for advanced apps.
  * Used by companies like Uber and Adobe.
* **Example**: A blog where pages are pre-rendered (SSG) or rendered server-side (SSR).

#### 1.2 Setting Up Nuxt

Create a Nuxt project with Vite.

**Steps**:

```bash
npx nuxi@latest init nuxt-app
cd nuxt-app
npm install
npm run dev
```

* Opens `http://localhost:3000`.
*   Creates:

    ```
    nuxt-app/
    ├── pages/
    │   ├── index.vue
    ├── layouts/
    ├── app.vue
    ├── nuxt.config.ts
    ├── package.json
    ```

**Example (pages/index.vue)**:

```vue
<script>
export default {
  data() {
    return {
      message: 'Yo, Nuxt!',
    };
  },
};
</script>

<template>
  <div>
    <h1>{{ message }}</h1>
    <button @click="message = 'Nuxt Rocks!'">Change</button>
  </div>
</template>

<style scoped>
h1 {
  color: #2b6cb0;
}
</style>
```

**Exercise**:

1. Create a Nuxt project.
2. Add a page `pages/about.vue` with a “About Us” heading.

**Answer**:

```vue
<!-- pages/about.vue -->
<template>
  <div>
    <h1>About Us</h1>
  </div>
</template>
```

* Access at `http://localhost:3000/about`.

***

### Part 2: Pages and Layouts

#### 2.1 Pages

Nuxt uses file-based routing. Files in `pages/` become routes.

**Example**:

```vue
<!-- pages/index.vue -->
<template>
  <div>
    <h1>Home</h1>
    <NuxtLink to="/about">Go to About</NuxtLink>
  </div>
</template>
```

```vue
<!-- pages/about.vue -->
<template>
  <div>
    <h1>About</h1>
    <NuxtLink to="/">Back to Home</NuxtLink>
  </div>
</template>
```

**Exercise**:

1. Create a `pages/contact.vue` page with a “Contact Us” link to `/`.

**Answer**:

```vue
<!-- pages/contact.vue -->
<template>
  <div>
    <h1>Contact Us</h1>
    <NuxtLink to="/">Back to Home</NuxtLink>
  </div>
</template>
```

#### 2.2 Layouts

Layouts define reusable page structures.

**Example (layouts/default.vue)**:

```vue
<template>
  <div>
    <header>
      <nav>
        <NuxtLink to="/">Home</NuxtLink>
        <NuxtLink to="/about">About</NuxtLink>
      </nav>
    </header>
    <slot />
  </div>
</template>

<style scoped>
nav {
  margin-bottom: 20px;
}
nav a {
  margin-right: 10px;
  color: #2b6cb0;
  text-decoration: none;
}
nav a:hover {
  text-decoration: underline;
}
</style>
```

```vue
<!-- pages/index.vue -->
<script>
export default {
  layout: 'default',
};
</script>

<template>
  <div>
    <h1>Home</h1>
  </div>
</template>
```

**Exercise**:

1. Create a `layouts/custom.vue` with a footer and apply it to `pages/about.vue`.

**Answer**:

```vue
<!-- layouts/custom.vue -->
<template>
  <div>
    <slot />
    <footer>© 2025 Nuxt App</footer>
  </div>
</template>
```

```vue
<!-- pages/about.vue -->
<script>
export default {
  layout: 'custom',
};
</script>

<template>
  <div>
    <h1>About</h1>
  </div>
</template>
```

***

### Part 3: Static Site Generation (SSG) and Server-Side Rendering (SSR)

#### 3.1 Static Site Generation (SSG)

Use `asyncData` for SSG.

**Example (pages/posts.vue)**:

```vue
<script>
export default {
  async asyncData() {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts');
    const posts = await res.json();
    return { posts };
  },
};
</script>

<template>
  <div>
    <h1>Posts</h1>
    <ul>
      <li v-for="post in posts" :key="post.id">
        <NuxtLink :to="`/posts/${post.id}`">{{ post.title }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>
```

**Exercise**:

1. Create a `pages/users.vue` page that fetches users from `https://jsonplaceholder.typicode.com/users`.

**Answer**:

```vue
<script>
export default {
  async asyncData() {
    const res = await fetch('https://jsonplaceholder.typicode.com/users');
    const users = await res.json();
    return { users };
  },
};
</script>

<template>
  <div>
    <h1>Users</h1>
    <ul>
      <li v-for="user in users" :key="user.id">{{ user.name }}</li>
    </ul>
  </div>
</template>
```

#### 3.2 Server-Side Rendering (SSR)

Nuxt enables SSR by default. Use `asyncData` for server-side data fetching.

**Example (pages/news.vue)**:

```vue
<script>
export default {
  async asyncData() {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts');
    const news = await res.json();
    return { news };
  },
};
</script>

<template>
  <div>
    <h1>News</h1>
    <ul>
      <li v-for="item in news" :key="item.id">{{ item.title }}</li>
    </ul>
  </div>
</template>
```

**Exercise**:

1. Create a `pages/todos.vue` page with SSR for todos from `https://jsonplaceholder.typicode.com/todos`.

***

### Part 4: Vuex in Nuxt

Nuxt integrates Vuex automatically.

**Example (store/index.js)**:

```javascript
export const state = () => ({
  count: 0,
});

export const mutations = {
  increment(state) {
    state.count++;
  },
};

export const actions = {
  increment({ commit }) {
    commit('increment');
  },
};

export const getters = {
  count: (state) => state.count,
};
```

```vue
<!-- pages/index.vue -->
<script>
export default {
  computed: {
    count() {
      return this.$store.getters.count;
    },
  },
};
</script>

<template>
  <div>
    <h1>Count: {{ count }}</h1>
    <button @click="$store.dispatch('increment')">Add</button>
  </div>
</template>
```

**Exercise**:

1. Add a Vuex action to reset `count`.

**Answer**:

```javascript
// store/index.js
export const state = () => ({
  count: 0,
});

export const mutations = {
  increment(state) {
    state.count++;
  },
  reset(state) {
    state.count = 0;
  },
};

export const actions = {
  increment({ commit }) {
    commit('increment');
  },
  reset({ commit }) {
    commit('reset');
  },
};
```

```vue
<!-- pages/index.vue -->
<template>
  <div>
    <h1>Count: {{ count }}</h1>
    <button @click="$store.dispatch('increment')">Add</button>
    <button @click="$store.dispatch('reset')">Reset</button>
  </div>
</template>
```

***

### Part 5: Project Setup

1. **Install Node.js**: [Download LTS](https://nodejs.org).
2.  **Create Project**:

    ```bash
    npx nuxi@latest init nuxt-blog
    cd nuxt-blog
    npm install
    npm run dev
    ```
3. Open `http://localhost:3000`.

**Structure**:

```
nuxt-blog/
├── pages/
├── layouts/
├── store/
├── app.vue
├── nuxt.config.ts
├── package.json
```

***

### Part 6: Project: Nuxt.js Blog

**Goal**: Build a blog with SSG for post lists and SSR for post details.

**Code (app.vue)**:

```vue
<template>
  <div class="container">
    <header>
      <nav>
        <NuxtLink to="/">Home</NuxtLink>
        <NuxtLink to="/posts">Posts</NuxtLink>
      </nav>
    </header>
    <NuxtPage />
  </div>
</template>

<style scoped>
.container {
  max-width: 800px;
  margin: 20px auto;
  padding: 20px;
}
nav {
  margin-bottom: 20px;
}
nav a {
  margin-right: 10px;
  color: #2b6cb0;
  text-decoration: none;
}
nav a:hover {
  text-decoration: underline;
}
</style>
```

**Code (pages/index.vue)**:

```vue
<template>
  <div>
    <h1>Welcome to the Blog</h1>
    <p>Check out our <NuxtLink to="/posts">posts</NuxtLink>.</p>
  </div>
</template>
```

**Code (pages/posts/index.vue)**:

```vue
<script>
export default {
  async asyncData() {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts');
    const posts = await res.json();
    return { posts };
  },
};
</script>

<template>
  <div>
    <h1>Blog Posts</h1>
    <ul>
      <li v-for="post in posts" :key="post.id">
        <NuxtLink :to="`/posts/${post.id}`">{{ post.title }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>

<style scoped>
ul {
  list-style: none;
  padding: 0;
}
li {
  margin: 10px 0;
}
</style>
```

**Code (pages/posts/\[id].vue)**:

```vue
<script>
export default {
  async asyncData({ params }) {
    const res = await fetch(
      `https://jsonplaceholder.typicode.com/posts/${params.id}`
    );
    const post = await res.json();
    return { post };
  },
};
</script>

<template>
  <div>
    <h1>{{ post.title }}</h1>
    <p>{{ post.body }}</p>
    <NuxtLink to="/posts">Back to Posts</NuxtLink>
  </div>
</template>
```

**Steps**:

1. Set up the project (Part 5).
2. Create `pages/index.vue`, `pages/posts/index.vue`, `pages/posts/[id].vue`, `app.vue`.
3. Run `npm run dev`.

**Exercises**:

1. Add a “Back to Home” link in `posts/[id].vue`.
2. Use Vuex to store posts.
3. Add Tailwind CSS for styling.

**Answer (Back to Home)**:

```vue
<!-- pages/posts/[id].vue -->
<template>
  <div>
    <h1>{{ post.title }}</h1>
    <p>{{ post.body }}</p>
    <NuxtLink to="/posts">Back to Posts</NuxtLink>
    <NuxtLink to="/">Back to Home</NuxtLink>
  </div>
</template>
```

***

### Part 7: Pro Practices

#### 7.1 Optimization

* **SSG**: Run `npm run generate` for static sites.
* **SSR**: Use `npm run build` and `npm run start` for server-side apps.
* **Code Splitting**: Nuxt handles this automatically.

#### 7.2 Debugging

* Use Vue Devtools for Nuxt components.
* Check server logs for SSR issues.

#### 7.3 Deployment

* **Static**: Deploy `dist/` to Netlify or Vercel.
* **SSR**: Deploy to Vercel or a Node.js server.

***

### Part 8: Next Steps

1. **Advanced Nuxt**: Explore Nuxt modules (e.g., `@nuxt/content`).
2. **Integrations**: Use with NestJS, TypeScript, Tailwind.
3. **Projects**: Build a portfolio or e-commerce site.
4. **Resources**:
   * [Nuxt.js Docs](https://nuxt.com)
   * X’s #NuxtJS tag for community tips

***

### Conclusion

You’ve mastered Nuxt.js: pages, layouts, SSG, SSR, and Vuex integration. The blog project applies these skills in a real-world app. Keep practicing by extending the project or building new Nuxt apps. Search X for #NuxtJS if you’re stuck, or ask me for help!
