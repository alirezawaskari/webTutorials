---
description: Build a Simple Blog App
---

# Django Tutorial

This tutorial teaches you how to build a simple blog application using **Django**, a Python web framework, with **CRUD functionality** (Create, Read, Update, Delete). It’s designed for total beginners, assuming you know basic Python but nothing about Django or web development. We’ll use Django’s **Model-View-Template (MVT)** pattern, HTML for templates, and SQLite as the default database. Each step includes clear explanations, code, and an exercise to practice.

***

### What You’ll Build

A blog app where you can:

* **Create** a new post (title and content).
* **Read** all posts or view one post’s details.
* **Update** an existing post.
* **Delete** a post.
* Manage posts via Django’s admin panel.

Think of it like a toy box: you add toys (posts), look at them, change their names, or throw them away!

***

### Step 1: Set Up Your Environment

1.  **Install Python**: Ensure Python (3.10 or higher) is installed. Check with:

    ```bash
    python --version
    ```
2.  **Install Django**: In your terminal, run:

    ```bash
    pip install django
    ```
3.  **Create a Project**: Start a Django project called `myblog`.

    ```bash
    django-admin startproject myblog
    cd myblog
    ```
4.  **Create an App**: Apps are small parts of your project. Create one called `blog`.

    ```bash
    python manage.py startapp blog
    ```
5.  **Register the App**: Open `myblog/myblog/settings.py` and add `'blog'` to `INSTALLED_APPS`:

    ```python
    INSTALLED_APPS = [
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        'blog',
    ]
    ```

***

### Step 2: Create a Model (Your Data)

A **model** is like a blueprint for your data. We’ll create a `Post` model with a title, content, and creation date.

In `myblog/blog/models.py`, add:

```python
from django.db import models

class Post(models.Model):
    title = models.CharField(max_length=200)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.title
```

* **Explanation**:
  * `title`: A short name (up to 200 characters).
  * `content`: The post’s text (longer text).
  * `created_at`: When the post was made (set automatically).
  * `__str__`: Shows the title when viewing the post.

Apply the model to the database:

```bash
python manage.py makemigrations
python manage.py migrate
```

***

### Step 3: Create Views (What to Show)

**Views** decide what happens when someone visits your site. We’ll create:

* A list view (show all posts).
* A detail view (show one post).
* Create, update, and delete views.

In `myblog/blog/views.py`, add:

```python
from django.shortcuts import render, get_object_or_404, redirect
from .models import Post
from .forms import PostForm

def post_list(request):
    posts = Post.objects.all()
    return render(request, 'blog/post_list.html', {'posts': posts})

def post_detail(request, pk):
    post = get_object_or_404(Post, pk=pk)
    return render(request, 'blog/post_detail.html', {'post': post})

def post_create(request):
    if request.method == 'POST':
        form = PostForm(request.POST)
        if form.is_valid():
            form.save()
            return redirect('post_list')
    else:
        form = PostForm()
    return render(request, 'blog/post_form.html', {'form': form})

def post_update(request, pk):
    post = get_object_or_404(Post, pk=pk)
    if request.method == 'POST':
        form = PostForm(request.POST, instance=post)
        if form.is_valid():
            form.save()
            return redirect('post_list')
    else:
        form = PostForm(instance=post)
    return render(request, 'blog/post_form.html', {'form': form})

def post_delete(request, pk):
    post = get_object_or_404(Post, pk=pk)
    if request.method == 'POST':
        post.delete()
        return redirect('post_list')
    return render(request, 'blog/post_delete.html', {'post': post})
```

* **Explanation**:
  * `post_list`: Gets all posts and shows them in a template.
  * `post_detail`: Shows one post by its ID (`pk`).
  * `post_create`: Handles a form to make a new post.
  * `post_update`: Updates an existing post.
  * `post_delete`: Deletes a post after confirmation.

***

### Step 4: Create a Form

Forms let users add or edit posts. Create a new file `myblog/blog/forms.py`:

```python
from django import forms
from .models import Post

class PostForm(forms.ModelForm):
    class Meta:
        model = Post
        fields = ['title', 'content']
```

* **Explanation**: Creates a form for the `title` and `content` fields of the `Post` model.

***

### Step 5: Create Templates (The Look)

Templates are HTML files that display your data. Create a folder `myblog/blog/templates/blog/` and add these files:

#### base.html (Main layout)

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Blog</title>
</head>
<body>
    <h1>My Blog</h1>
    <a href="{% url 'post_list' %}">Home</a>
    <a href="{% url 'post_create' %}">New Post</a>
    {% block content %}
    {% endblock %}
</body>
</html>
```

#### post\_list.html (Show all posts)

```html
{% extends 'blog/base.html' %}
{% block content %}
    <h2>All Posts</h2>
    <ul>
    {% for post in posts %}
        <li><a href="{% url 'post_detail' post.pk %}">{{ post.title }}</a></li>
    {% endfor %}
    </ul>
{% endblock %}
```

#### post\_detail.html (Show one post)

```html
{% extends 'blog/base.html' %}
{% block content %}
    <h2>{{ post.title }}</h2>
    <p>{{ post.content }}</p>
    <p>Posted on: {{ post.created_at }}</p>
    <a href="{% url 'post_update' post.pk %}">Edit</a>
    <a href="{% url 'post_delete' post.pk %}">Delete</a>
{% endblock %}
```

#### post\_form.html (Create/Edit form)

```html
{% extends 'blog/base.html' %}
{% block content %}
    <h2>{% if form.instance.pk %}Edit{% else %}New{% endif %} Post</h2>
    <form method="post">
        {% csrf_token %}
        {{ form.as_p }}
        <button type="submit">Save</button>
    </form>
{% endblock %}
```

#### post\_delete.html (Confirm delete)

```html
{% extends 'blog/base.html' %}
{% block content %}
    <h2>Delete {{ post.title }}?</h2>
    <form method="post">
        {% csrf_token %}
        <button type="submit">Yes, Delete</button>
        <a href="{% url 'post_list' %}">Cancel</a>
    </form>
{% endblock %}
```

* **Explanation**:
  * `base.html`: The main layout with a menu.
  * `post_list.html`: Lists all post titles as clickable links.
  * `post_detail.html`: Shows a post’s title, content, and date.
  * `post_form.html`: Form for adding or editing posts.
  * `post_delete.html`: Confirms before deleting a post.

***

### Step 6: Set Up URLs

URLs connect web addresses to views. Create a new file `myblog/blog/urls.py`:

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.post_list, name='post_list'),
    path('post/<int:pk>/', views.post_detail, name='post_detail'),
    path('post/new/', views.post_create, name='post_create'),
    path('post/<int:pk>/edit/', views.post_update, name='post_update'),
    path('post/<int:pk>/delete/', views.post_delete, name='post_delete'),
]
```

Link it to the project. In `myblog/myblog/urls.py`, update:

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('blog.urls')),
]
```

***

### Step 7: Run the App

1.  Start the Django development server:

    ```bash
    python manage.py runserver
    ```
2. Open `http://127.0.0.1:8000/` in your browser to see your blog.
3. Try creating a post, viewing it, editing it, or deleting it.

***

### Step 8: Add Admin Access

Django’s admin panel lets you manage posts easily.

1.  Create a superuser:

    ```bash
    python manage.py createsuperuser
    ```
2. Follow prompts to set a username, email, and password.
3. In `myblog/blog/admin.py`, add:

```python
from django.contrib import admin
from .models import Post

admin.site.register(Post)
```

4. Visit `http://127.0.0.1:8000/admin/` and log in to manage posts.

***

### Exercise

1. Create a new Django project called `myfirstblog`.
2. Make a `Post` model with `title` (CharField, max\_length=200), `content` (TextField), and `author` (CharField, max\_length=100).
3. Set up a view and template to show all posts.
4. Add a link in `post_list.html` to a new page that says “Hello, Django!”.
5. Test it at `http://127.0.0.1:8000/`.

**Answer** (try it first, then check):

```python
# models.py
from django.db import models

class Post(models.Model):
    title = models.CharField(max_length=200)
    content = models.TextField()
    author = models.CharField(max_length=100)

    def __str__(self):
        return self.title

# views.py
from django.shortcuts import render
from .models import Post

def post_list(request):
    posts = Post.objects.all()
    return render(request, 'blog/post_list.html', {'posts': posts})

def hello_page(request):
    return render(request, 'blog/hello.html')

# urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('', views.post_list, name='post_list'),
    path('hello/', views.hello_page, name='hello_page'),
]

# templates/blog/post_list.html
<!DOCTYPE html>
<html>
<head>
    <title>My First Blog</title>
</head>
<body>
    <h1>My Blog</h1>
    <a href="{% url 'hello_page' %}">Say Hello</a>
    <ul>
    {% for post in posts %}
        <li>{{ post.title }} by {{ post.author }}</li>
    {% endfor %}
    </ul>
</body>
</html>

# templates/blog/hello.html
<!DOCTYPE html>
<html>
<head>
    <title>Hello</title>
</head>
<body>
    <h1>Hello, Django!</h1>
    <a href="{% url 'post_list' %}">Back to Posts</a>
</body>
</html>
```

Run migrations (`python manage.py makemigrations`, `python manage.py migrate`), start the server (`python manage.py runserver`), and test at `http://127.0.0.1:8000/`.

***

### Next Steps

* **Add CSS**: Style your templates with CSS (e.g., use Bootstrap).
* **Deploy**: Host your app on Heroku, Railway, or DigitalOcean.
* **Extend**: Add user authentication or comments (ask me for details!).

If you want to continue with **CSS**, **JavaScript**, or more Django features (e.g., user login, REST API), let me know! I can also tie this to your goal of becoming a **perfect web developer** with job-prep tips or tools like Vite.
