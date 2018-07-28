# Skeleton Router

The reason to use a router, is to show url paths as a response to user interaction,
however without making request to the server. This is very common in single page apps,
where you load all the data initially, and hide and show the relevant parts by the
user interaction. Let's use a router for out app:

```js
// initialize router
const router = Skeleton.Router();

// set paths and callback functions
router.path('/all', () => filterTodos('all'));
router.path('/active', () => filterTodos('active'));
router.path('/completed', () => filterTodos('completed'));
```

Now, remember this piece of html?

```html
<span id="filter-all" onClick="router.visit('/all')">All</span>
<span id="filter-active" onClick="router.visit('/active')">Active</span>
<span id="filter-completed" onClick="router.visit('/completed')">Completed</span>
```

What we did is simply defining what path we want to visit, means what path we want
the url to show, and what callback function we want to apply as this path is activated.
We have not yet defined the 'filterTodos' function, however this is clear what it meant
to happen here.

```js
router.path('/all', () => filterTodos('all'));
```

This means that when the path '/all' is visited, the 'filterTodos' function should
be invoked with parameter 'all'.

```js
router.visit('/all');
```

This means visiting the path we predefined, updating the url pathname, and invoking
the callback function we predefined.
