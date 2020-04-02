# Migrating from Particles.js to tsParticles

[tsParticles](https://github.com/matteobruni/tsparticles) is fully compatible with Particles.js and the migration is really easy to do.

Let's checkout your possible HTML code.

## Changing the script

You should have something like the following code

```html
<script src="particles.js"></script>
```

Well to migrate from particles.js to tsParticles all you have to do is replace that to this

```html
<script src="tsparticles.js"></script>
```

And you're done. Easy isn't it?

## Deprecation

The particlesJS identifier is deprecated in this library, well the library has a new name so it's changed.

Now let's checkout the Javascript code, you should have something like this

```javascript
/* particlesJS.load(@dom-id, @path-json, @callback (optional)); */
particlesJS.load('particles-js', 'assets/particles.json', function() {
  console.log('callback - particles.js config loaded');
});
```

or something like this

```javascript
particlesJS('particles-js', { /* your options here */ });
```

All you have to do to use the new identifiers it replacing the function

`particlesJS()` into `tsParticles.load()`

or the function

`particlesJS.load()` into `tsParticles.loadJSON()`

**Warning here**

*the tsParticles.load() returns the object you created*
*the `loadJSON` doesn't have a third parameter, if you need a callback use the `then` function, it returns a `Promise` with the loaded object as parameter.*

Still really simple.

Let's convert the sample provided above to understand

```javascript
/* particlesJS.load(@dom-id, @path-json, @callback (optional)); */
tsParticles.loadJSON('particles-js', 'assets/particles.json').then(function(p) {
  // p is the loaded container, for using it later
  console.log('callback - particles.js config loaded');
});

var p = tsParticles.load('particles-js', { /* your options here */ }); // p is the loaded container, for using it later
```

### Deprecated Properties

Some particlesJS identifiers are now deprecated, they were changed for improvements. I try to keep 100% compatibility and when a breaking change occurs I'll document it.

You can retrieve the container with `tsParticles.domItem(0)` or a different index if you have more than 1 and call the `exportConfiguration()` method.
It returns a **ready to use** `JSON string` with the current configuration with all the actual structure and all values you set.