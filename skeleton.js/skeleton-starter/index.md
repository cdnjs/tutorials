# First Page Load

The code to run on the first page load to fetched saved todos, and the filter
that signs what was the last url path we visited.
```js
{
	let todos = Skeleton.storage.fetch('todos');
	TodosList.pushAll(todos); // push all stored todos
	let filter = Skeleton.storage.fetch('filter') || 'all';
	router.visit(`/${filter}`); // go to last saved path
}
```