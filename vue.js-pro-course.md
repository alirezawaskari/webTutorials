---
description: From Zero to Expert
---

# Vue.js Pro Course

### Introduction

This course is for beginners with HTML, CSS, basic JavaScript (variables, functions, arrays), and some React knowledge. You’ll learn **Vue.js**, a progressive JavaScript framework for building user interfaces and single-page applications (SPAs). Vue is known for its simplicity, flexibility, and performance, making it ideal for modern web apps. By the end, you’ll master Vue’s core and advanced features, integrate it with Vite, and build a project to solidify your skills. This is a hands-on, no-BS guide to make you a Vue.js pro.

**What You’ll Learn**:

1. Vue.js basics (components, directives, data binding).
2. Advanced features (Vuex, Vue Router, Composition API).
3. Integration with Vite and TypeScript.
4. Best practices and optimization.
5. Project: A Vue.js task tracker app.

**Tools Needed**:

* **Node.js**: [Download LTS](https://nodejs.org) (installs `npm`).
* **VS Code**: [Free download](https://code.visualstudio.com/) with [Volar extension](https://marketplace.visualstudio.com/items?itemName=Vue.volar).
* A browser (Chrome recommended).

**How to Use This Document**:

* Save as `Vue_Pro_Course.md` or convert to PDF (e.g., VS Code with “Markdown PDF” extension).
* Follow each section, code the examples, and do the exercises.
* Set up a project (Part 5) to code along.
* Build the project in Part 6 to apply your skills.
* Refer to resources for extra learning.

**Time Commitment**: \~10-15 hours (spread over days/weeks).

***

### Part 1: Vue.js Basics

#### 1.1 What is Vue.js?

Vue.js is a **progressive JavaScript framework** for building user interfaces, focusing on the view layer. It’s lightweight, easy to learn, and supports SPAs and server-side rendering (SSR) with Nuxt.

* **Why Vue.js?**
  * Simple syntax, similar to HTML and JavaScript.
  * Component-based, like React, but more beginner-friendly.
  * Great for SPAs, universal apps, and integration with Nuxt/Nest.
  * Used by companies like GitLab and Alibaba.
* **Example**: A Vue component displaying a counter.

#### 1.2 Setting Up Vue with Vite

Use Vite for a fast development experience.

**Steps**:

```bash
npm create vite@latest vue-app -- --template vue
cd vue-app
npm install
npm run dev
```

* Opens `http://localhost:5173`.
*   Creates:

    ```
    vue-app/
    ├── src/
    │   ├── main.js
    │   ├── App.vue
    │   ├── style.css
    ├── index.html
    ├── vite.config.js
    ├── package.json
    ```

**Example (src/App.vue)**:

```vue
<script>
export default {
  data() {
    return {
      count: 0,
    };
  },
};
</script>

<template>
  <div>
    <h1>Yo, Vue!</h1>
    <p>Count: {{ count }}</p>
    <button @click="count++">Increment</button>
  </div>
</template>

<style scoped>
h1 {
  color: #2b6cb0;
}
</style>
```

* `data()`: Reactive state.
* `{{ count }}`: Two-way data binding.
* `@click`: Event handling.

**Exercise**:

1. Create a Vue project with Vite.
2. Add a button to decrease `count`.

**Answer**:

```vue
<script>
export default {
  data() {
    return {
      count: 0,
    };
  },
};
</script>

<template>
  <div>
    <h1>Yo, Vue!</h1>
    <p>Count: {{ count }}</p>
    <button @click="count++">Increment</button>
    <button @click="count--">Decrement</button>
  </div>
</template>
```

***

### Part 2: Vue Components and Directives

#### 2.1 Components

Components are reusable, encapsulated UI pieces.

**Example (src/components/Counter.vue)**:

```vue
<script>
export default {
  props: ['initialCount'],
  data() {
    return {
      count: this.initialCount || 0,
    };
  },
};
</script>

<template>
  <div>
    <p>Count: {{ count }}</p>
    <button @click="count++">Add</button>
  </div>
</template>
```

```vue
<!-- src/App.vue -->
<script>
import Counter from './components/Counter.vue';

export default {
  components: { Counter },
};
</script>

<template>
  <div>
    <h1>Vue App</h1>
    <Counter :initialCount="5" />
  </div>
</template>
```

**Exercise**:

1. Create a `Greeting.vue` component with a `name` prop to display “Hello, \[name]!”.

**Answer**:

```vue
<!-- src/components/Greeting.vue -->
<script>
export default {
  props: ['name'],
};
</script>

<template>
  <p>Hello, {{ name || 'stranger' }}!</p>
</template>
```

```vue
<!-- src/App.vue -->
<script>
import Greeting from './components/Greeting.vue';

export default {
  components: { Greeting },
};
</script>

<template>
  <div>
    <Greeting name="Dude" />
  </div>
</template>
```

#### 2.2 Directives

Vue directives (e.g., `v-bind`, `v-on`, `v-if`) control DOM behavior.

**Example**:

```vue
<script>
export default {
  data() {
    return {
      show: true,
      message: 'Yo!',
    };
  },
};
</script>

<template>
  <div>
    <input v-model="message" placeholder="Type here" />
    <p v-if="show">{{ message }}</p>
    <button @click="show = !show">Toggle</button>
  </div>
</template>
```

* `v-model`: Two-way binding.
* `v-if`: Conditional rendering.

**Exercise**:

1. Create a component with an input and a button to toggle visibility of the input text.

**Answer**:

```vue
<script>
export default {
  data() {
    return {
      text: '',
      isVisible: true,
    };
  },
};
</script>

<template>
  <div>
    <input v-model="text" placeholder="Enter text" />
    <p v-if="isVisible">{{ text }}</p>
    <button @click="isVisible = !isVisible">Toggle</button>
  </div>
</template>
```

***

### Part 3: Vue Router

Add client-side routing with Vue Router.

**Setup**:

```bash
npm install vue-router@4
```

```javascript
// src/router/index.js
import { createRouter, createWebHistory } from 'vue-router';
import Home from '../views/Home.vue';
import About from '../views/About.vue';

const routes = [
  { path: '/', component: Home },
  { path: '/about', component: About },
];

export default createRouter({
  history: createWebHistory(),
  routes,
});
```

```javascript
// src/main.js
import { createApp } from 'vue';
import App from './App.vue';
import router from './router';

createApp(App).use(router).mount('#app');
```

```vue
<!-- src/App.vue -->
<template>
  <div>
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </nav>
    <router-view />
  </div>
</template>
```

```vue
<!-- src/views/Home.vue -->
<template>
  <h1>Home Page</h1>
</template>
```

```vue
<!-- src/views/About.vue -->
<template>
  <h1>About Page</h1>
</template>
```

**Exercise**:

1. Add a `/contact` route with a “Contact Us” page.

**Answer**:

```javascript
// src/router/index.js
const routes = [
  { path: '/', component: Home },
  { path: '/about', component: About },
  { path: '/contact', component: Contact },
];
```

```vue
<!-- src/views/Contact.vue -->
<template>
  <h1>Contact Us</h1>
</template>
```

***

### Part 4: Vuex for State Management

Manage app-wide state with Vuex.

**Setup**:

```bash
npm install vuex@4
```

```javascript
// src/store/index.js
import { createStore } from 'vuex';

export default createStore({
  state: {
    count: 0,
  },
  mutations: {
    increment(state) {
      state.count++;
    },
  },
  actions: {
    increment({ commit }) {
      commit('increment');
    },
  },
  getters: {
    count: (state) => state.count,
  },
});
```

```javascript
// src/main.js
import { createApp } from 'vue';
import App from './App.vue';
import store from './store';
import router from './router';

createApp(App).use(store).use(router).mount('#app');
```

```vue
<!-- src/App.vue -->
<script>
import { useStore } from 'vuex';

export default {
  setup() {
    const store = useStore();
    return {
      count: store.getters.count,
      increment: () => store.dispatch('increment'),
    };
  },
};
</script>

<template>
  <div>
    <h1>Vuex Counter</h1>
    <p>Count: {{ count }}</p>
    <button @click="increment">Add</button>
  </div>
</template>
```

**Exercise**:

1. Add a Vuex mutation to reset `count` to 0.

**Answer**:

```javascript
// src/store/index.js
mutations: {
  increment(state) {
    state.count++;
  },
  reset(state) {
    state.count = 0;
  },
},
actions: {
  increment({ commit }) {
    commit('increment');
  },
  reset({ commit }) {
    commit('reset');
  },
},
```

```vue
<!-- src/App.vue -->
<script>
import { useStore } from 'vuex';

export default {
  setup() {
    const store = useStore();
    return {
      count: store.getters.count,
      increment: () => store.dispatch('increment'),
      reset: () => store.dispatch('reset'),
    };
  },
};
</script>

<template>
  <div>
    <h1>Vuex Counter</h1>
    <p>Count: {{ count }}</p>
    <button @click="increment">Add</button>
    <button @click="reset">Reset</button>
  </div>
</template>
```

***

### Part 5: Project Setup

1. **Install Node.js**: [Download LTS](https://nodejs.org).
2.  **Create Project**:

    ```bash
    npm create vite@latest vue-app -- --template vue
    cd vue-app
    npm install vue-router@4 vuex@4
    npm run dev
    ```
3. Create `src/views/Home.vue`, `src/views/About.vue`, `src/router/index.js`, `src/store/index.js`.
4. Open `http://localhost:5173`.

**Structure**:

```
vue-app/
├── src/
│   ├── components/
│   ├── views/
│   ├── router/
│   ├── store/
│   ├── App.vue
│   ├── main.js
│   ├── style.css
├── public/
├── vite.config.js
├── package.json
```

***

### Part 6: Project: Vue.js Task Tracker

**Goal**: Build a task tracker app with Vue, Vuex, and Vue Router.

**Code (src/App.vue)**:

```vue
<script>
import { useStore } from 'vuex';
import { useRouter } from 'vue-router';

export default {
  setup() {
    const store = useStore();
    const router = useRouter();
    return {
      tasks: store.getters.tasks,
      addTask: (task) => store.dispatch('addTask', task),
      toggleTask: (id) => store.dispatch('toggleTask', id),
      navigate: (path) => router.push(path),
    };
  },
};
</script>

<template>
  <div class="container">
    <nav>
      <router-link to="/">Tasks</router-link>
      <router-link to="/add">Add Task</router-link>
    </nav>
    <router-view />
  </div>
</template>

<style scoped>
.container {
  max-width: 600px;
  margin: 20px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
}
nav {
  margin-bottom: 20px;
}
nav a {
  margin-right: 10px;
  text-decoration: none;
  color: #2b6cb0;
}
nav a:hover {
  text-decoration: underline;
}
</style>
```

**Code (src/views/TaskList.vue)**:

```vue
<script>
import { useStore } from 'vuex';

export default {
  setup() {
    const store = useStore();
    return {
      tasks: store.getters.tasks,
      toggleTask: (id) => store.dispatch('toggleTask', id),
    };
  },
};
</script>

<template>
  <div>
    <h1>Task Tracker</h1>
    <ul>
      <li
        v-for="task in tasks"
        :key="task.id"
        :class="{ done: task.done }"
        @click="toggleTask(task.id)"
      >
        {{ task.text }}
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
  padding: 10px;
  border-bottom: 1px solid #eee;
  cursor: pointer;
}
.done {
  text-decoration: line-through;
  color: #888;
}
</style>
```

**Code (src/views/AddTask.vue)**:

```vue
<script>
import { useStore } from 'vuex';
import { useRouter } from 'vue-router';

export default {
  setup() {
    const store = useStore();
    const router = useRouter();
    let text = '';
    return {
      text,
      addTask: () => {
        if (text.trim()) {
          store.dispatch('addTask', { id: Date.now(), text, done: false });
          text = '';
          router.push('/');
        }
      },
    };
  },
};
</script>

<template>
  <div>
    <h1>Add Task</h1>
    <input v-model="text" placeholder="New task" @keyup.enter="addTask" />
    <button @click="addTask">Add</button>
  </div>
</template>

<style scoped>
input {
  padding: 8px;
  width: 70%;
  margin-right: 10px;
}
button {
  padding: 8px 16px;
  background-color: #2b6cb0;
  color: white;
  border: none;
  border-radius: 4px;
}
button:hover {
  background-color: #2c5282;
}
</style>
```

**Code (src/store/index.js)**:

```javascript
import { createStore } from 'vuex';

export default createStore({
  state: {
    tasks: [],
  },
  mutations: {
    addTask(state, task) {
      state.tasks.push(task);
    },
    toggleTask(state, id) {
      state.tasks = state.tasks.map((task) =>
        task.id === id ? { ...task, done: !task.done } : task
      );
    },
  },
  actions: {
    addTask({ commit }, task) {
      commit('addTask', task);
    },
    toggleTask({ commit }, id) {
      commit('toggleTask', id);
    },
  },
  getters: {
    tasks: (state) => state.tasks,
  },
});
```

**Steps**:

1. Set up the project (Part 5).
2. Create `src/views/TaskList.vue`, `src/views/AddTask.vue`, `src/router/index.js`, `src/store/index.js`.
3. Replace `src/App.vue` with the code above.
4. Run `npm run dev`.

**Exercises**:

1. Add a “Clear All” button to reset tasks.
2. Persist tasks in localStorage.
3. Add a route for a “Completed Tasks” page.

**Answer (Clear All)**:

```javascript
// src/store/index.js
mutations: {
  addTask(state, task) {
    state.tasks.push(task);
  },
  toggleTask(state, id) {
    state.tasks = state.tasks.map((task) =>
      task.id === id ? { ...task, done: !task.done } : task
    );
  },
  clearAll(state) {
    state.tasks = [];
  },
},
actions: {
  addTask({ commit }, task) {
    commit('addTask', task);
  },
  toggleTask({ commit }, id) {
    commit('toggleTask', id);
  },
  clearAll({ commit }) {
    commit('clearAll');
  },
},
```

```vue
<!-- src/views/TaskList.vue -->
<template>
  <div>
    <h1>Task Tracker</h1>
    <button @click="$store.dispatch('clearAll')">Clear All</button>
    <ul>
      <li
        v-for="task in tasks"
        :key="task.id"
        :class="{ done: task.done }"
        @click="toggleTask(task.id)"
      >
        {{ task.text }}
      </li>
    </ul>
  </div>
</template>
```

***

### Part 7: Pro Practices

#### 7.1 Optimization

* **Code Splitting**: Use dynamic imports (`const Comp = () => import('./Comp.vue')`).
* **Production Build**: Run `npm run build` for optimized bundles.
* **Tree Shaking**: Vite handles this automatically.

#### 7.2 Debugging

* Use Chrome DevTools with Vue Devtools extension.
* Enable source maps in `vite.config.js`.

#### 7.3 Deployment

* Build: `npm run build`.
* Deploy `dist/` to Vercel or Netlify.

***

### Part 8: Next Steps

1. **Advanced Vue**: Explore Composition API, TypeScript integration.
2. **Integrations**: Use with Nuxt.js, NestJS, or Pinia.
3. **Projects**: Build a portfolio or dashboard.
4. **Resources**:
   * [Vue.js Docs](https://vuejs.org)
   * X’s #VueJS tag for community tips

***

### Conclusion

You’ve mastered Vue.js: components, directives, Vuex, and Vue Router. The task tracker project applies these skills in a real-world app. Keep practicing by extending the project or building new Vue apps. Search X for #VueJS if you’re stuck, or ask me for help!
