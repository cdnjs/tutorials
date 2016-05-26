# Setting up the Html and the template for our app

Lets's start with the 'html' body:
```html
<body>
  <div class="todos-header">
    <span onClick="removeAll()">Remove All</span>
  </div>
  <form name="todo-form">
    <input type="text" placeholder="What needs to be done?" id="todo-input" />
  </form>
  <div id="todo-list"></div>
  <div class="todos-footer">
    <span id="todos-size">0</span> items left
    <span id="filter-all" onClick="router.visit('/all')">All</span>
    <span id="filter-active" onClick="router.visit('/active')">Active</span>
    <span id="filter-completed" onClick="router.visit('/completed')">Completed</span>
    <buton onClick="clearCompleted()">Clear Completed</span>
  </div>
</body>
```
Now let's go over it and break it into parts:
Functions: 'removeAll' todos, 'clearCompleted' todos. 
Forms: A 'todo-form' to submit a new todo.
Lists: A 'todo-list' element which will be the container of our todos. 
We also have 'all', 'active' and 'completed' filters (The 'router.visit' explained later).

---
Ok, now let's define our 'todo-template':
```html
<!-- Todo Template -->
<template id="todo-template">
  <div data-id="{{ index }}">
    <input type="checkbox" onChange="toggleTodo({{ index }})" data-checked="isCompleted" />
    <span onDblclick="editTodo({{ index }})" 
        data-hide="isEditing" 
        data-class='{"done": "isCompleted", "bold": "!isCompleted"}'
    >
      {{ text | capitalize }}
    </span>
    <input type="text" onKeyup="setEditedTodo(event, {{ index }})" value="{{ text }}" data-show="isEditing" />
    <button onClick="removeTodo({{ index }})">x</button>
  </div>
</template>
```
Now notice that a template is attached to a model, which we will define in the next article.
When you define a template, you actually tell how each model will look. The way to seperate
templates when they get rendered is by using 'index', which is provided by Skeleton.js for free.
What you see inside '{{ }}' will get rendered as you push an object to the list array.

---
Let's define a model, and continue exploring what we see in the template:
```js
let TodoModel = Skeleton.Model({
  defaults: {
    text: '',
    isCompleted: false,
    isEditing: false
  },
  init() {
    console.log(`Todo text is: ${this.get('text')}, isCompleted: ${this.get('isCompleted')}`);
  }
});
```
The only object needed is the defaults object, to specify constant and changing model fields.
Each of our models has 'text', 'isCompleted' and 'isEditing' fields.
The 'init' function is called each time a model is initialized.

---
Now, we need to define a list. A skeleton list object is what we are going to work with in all
phases of the application.
```js
let TodosList = Skeleton.List({
  model: TodoModel,
  element: 'todo-list',
  template: {templateId: 'todo-template'}
});
```
* 'model': The model that builds the list.
* 'element': The html element that will contain the list models.
* 'template': A string, or an object with templateId field to specify the template.