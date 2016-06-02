# Our TodoMVC Functions

Let's look at our todo-template:
```js
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

And now let's start defining our functions:

* removeTodo
```js
window.removeTodo = (index) => {
	TodosList.remove(index);
}
```
Since we render the todo index, we can pass it to the built in 'remove' function of 'Skeleton.List',
and remove it making the list rerender without this todo. Please notice that in order to use built in
'remove' and 'edit' functions, you need to provide the template model a 'data-id' attribute.

* toggleTodo
```js
window.toggleTodo = (index) => {
	let isCompleted = !TodosList.get(index).isCompleted;
	TodosList.edit(index, { isCompleted }); // Edit todo
}
```
When the checkbox is clicked, we edit the todo. In order to also make it apper, we use the skeleton 'data-checked'
attribute that gets a boolean and updates when we edit our todo.

* editTodo
```js
window.editTodo = (index) => {
	if(TodosList.get(index).isCompleted) {
		return;
	}
	TodosList.edit(index, { isEditing: true });
}
```
We update the todo to tell the template to show and hide some parts as we edit. Notice the 'data-show' and
'data-hide' attributes in the template depending on 'isEditing' boolean value.

* setEditedTodo
```js
window.setEditedTodo = (event, index) => {
	if(event.keyCode === 13) { // enter key code
		let text = event.target.value;
		if(!text || !text.trim())	{
			return;
		}
		TodosList.edit(index, { text , isEditing: false });
		event.target.value = '';
	}
	else if(event.keyCode === 27) { // escape key code
		TodosList.edit(index, { isEditing: false });
	}
}
```
Now on this function, we pass the event also. If enter key is pressed, we edit the todo text,
and if escape key is pressed, we quit the editing mode.

* filterTodos

```js
window.filterTodos = (type) => {
	if(type === 'all') {
		TodosList.filter(todo => true);
	} else if(type === 'active') {
		TodosList.filter(todo => !todo.isCompleted);
	} else { 
		TodosList.filter(todo => todo.isCompleted);
	}
	_styleFilter(type);
	Skeleton.storage.save({ filter: type });
}

// Style on choosing filter
const filters = {
	all: document.getElementById('filter-all'),
	active: document.getElementById('filter-active'),
	completed: document.getElementById('filter-completed')
}

function _styleFilter(filter) {
	Object.keys(filters).forEach(fltr => {
		if(fltr === filter) {
			return filters[fltr].style.fontStyle = 'italic';
		}
		return filters[fltr].style.fontStyle = 'normal';
	});
}
```

Filtering todos is done by using the built in 'filter' method. We give it a relevant callback to each
filter type passed. Then, we style the chosed filter and store the filter in localStorage.
Skeleton provides a simple API to saving, fetching and clearing data to/from browser localStorage.

* clearCompleted
```js
window.clearCompleted = () => {
	TodosList.forEach(todo => {
		if(todo.isCompleted) {
			window.removeTodo(todo.index);
		}
	});
}
```
Here, we simply iterate over the todos, and if a todo is completed,
we clear it by its index.

* removeAll
```js
window.removeAll = () => {
	TodosList.removeAll();
}
```
Very easy to remove all models. Simply use the built in 'removeAll' function.

* updateSize

```js
var todosSize = document.getElementById('todos-size');
window.updateSize = () => {
	todosSize.textContent = TodosList.models().filter(todo => !todo.isCompleted).length;
} 
```
This is a function we want to run to update the size of the todos list after any interaction that may change it.
When we type 'TodosList.models()' we get the actual models of the todos list.