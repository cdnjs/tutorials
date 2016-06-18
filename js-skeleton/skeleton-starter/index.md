# First Page Load

On the first page load, we want to fetch saved todos from localStorage, and display them
after filtering by the last visited route. So, we retrieve the todos, push them all,
retrieve the filter and applying the router on it.
Here is the code snippet:

```js
let todos = Skeleton.storage.fetch('todos') || [];
TodosList.pushAll(todos); // push all stored todos
let filter = Skeleton.storage.fetch('filter') || 'all';
router.visit(`/${filter}`); // go to last saved path
```
