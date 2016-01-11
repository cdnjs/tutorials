# Getting started with VisSense.js
VisSense.js is a utility library for observing visibility changes of DOM elements. 
It let's you immediately know when an element becomes hidden, partly visible or fully visible.

It is lightweight (<4KB minified and gzipped), tested and documented. Best of all: No dependencies.
What it does

VisSense.js satisfies three requirements:
* provide methods for detecting visibility of DOM elements
* provide a convenience class with straightforward methods (like isHidden, isVisible, isFullyVisible)
* provide a convenience class for detecting changes in visibility

## Download
VisSense.js can be retrieved via various ways. You can either download it using your
favourite packaging tool, directly from Github or by referencing it from a cdn provider
(like cdnjs.com).

### Github
See the [Releases page on Github](https://github.com/vissense/vissense/releases) to see the latest and all past releases.

### npm
`npm install vissense/vissense --save`

### Bower
`bower install vissense/vissense --save`

### cdnjs
See hosted version of [VisSense.js on cdnjs.com](https://cdnjs.com/libraries/vissense).

## Basic usage
VisSense.js is a small and powerful library with an easy interface. 
To get started you only need to memorize the following four methods:
- `isHidden`
- `isVisible`
- `isFullyVisible`
- `percentage`

The first three methods return boolean values and their names are quite self-explanatory.
`isHidden` returns `true` if **no area of the target element** is currently in the viewport of the user.
`isVisible` returns `true` if **any area of the target element** is in the viewport.
`isFullyVisible` returns `true` if **the whole surface area of the element** is in the viewport.

The `percentage` method returns a floating point number representing the target elements currently visible surface area in the viewport of the user's 
browser as percentage. 
If the element is not visible `0` is returned. 
If the element is fully visible `1` is returned. 
If only a quarter of the element is visible the method returns `0.25`. 
Likewise if three quarters are visible the method returns `0.75` is returned.

## Simple example

Say you want to know whether a user read your whole article or blog post. For demonstrating purposes we assume that whenever the footer is visible the user has been reading everything from top to bottom (of course it just means that the user *scrolled* to the end - not necessarily reading every paragraph).
How can one archive that? See the following code snippet:
```js
var myFooterElement = document.getElementById('footer');
var footerElementArea = VisSense(myFooterElement);
var isFooterVisible = footerElementArea.isVisible();

if (isFooterVisible) {
    ...
}
```

Of course this is much more readable with a simple one-liner:
```js
var isFooterVisible = VisSense(document.getElementById('footer')).isVisible();
```

Easy, isn't it? That's how you determine whether an element is visible with VisSense.js.
If you want to know how you can observe visibility changes over time follow the next chapter
on ['How to autoplay a video when it becomes visible'](https://cdnjs.com/libraries/vissense/tutorials/autoplay-video).




