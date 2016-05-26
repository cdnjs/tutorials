# What it means to subscribe to events?

Subscription to list events in Skeleton.js means firing callback functions when a specified event
occures. This is very usefull for updating parts of the DOM that are dependent on list actions.

---
For instance, when we 'push' or 'edit' a todo, we want to filter our todo list again:
```js
TodosList.subscribe(['push','edit'], () => {
	let filter = Skeleton.storage.fetch('filter') || 'all';
	if(filter) {
		window.filterTodos(filter);
	}
});
```

When we 'push','remove','edit','removeAll', we want to update the size of our todo list we show the user,
and resave our todos in the browser localStorage:
```js
TodosList.subscribe(['push','remove','edit','removeAll'], () => {
	updateSize();
	Skeleton.storage.save({ 
		todos: TodosList.models() 
	});
});
```

Finally, when we push an array of todos, we want to update the size of the todo list we show the user:
```js
TodosList.subscribe('pushAll', updateSize);
```