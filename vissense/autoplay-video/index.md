# How to autoplay a video when it becomes visible

In the [previous chapter](https://cdnjs.com/libraries/vissense/tutorials/getting-started) you saw how the current visibility of an element can be determined.
In this example we can see how you can monitor visibility changes over time.

Say you want to start a video when it is fully visible and stop it as soon as it is not visible anymore.

You can do this my using a VisSense `monitor`.
A monitor is an object observing the visibility of your element providing
the opportunity to react on certain events e.g.
visibility state changes (element becomes `hidden`, `visible` or `fullyvisible`),
percentage changes (visible area increases/decreases, etc.).
But you can even extend monitors with custom functionality and send your own events!

In this simplified example we will just react when the element either
becomes fully visible or goes completely off the screen becoming hidden.

```js
var myVideo = document.getElementById('myVideo');

VisSense.VisMon.Builder(VisSense(myVideo))
.on('fullyvisible', function() {
    myVideo.play();
})
.on('hidden', function() {
    myVideo.pause();
})
.build()
.start();
```

Simple as that. But what have we done?
The monitor comes with a nice builder style syntax.
So what we do is the following:

- Create an instance of a monitor *builder* and give it an instance of a VisSense object with our video.
- We register a 'play' and a 'pause' callback ...
- turn the builder into a monitor object with `build()` ...
- and immediately start it  with `start()`

Here is more verbose version with comments (waaay too verbose):

```js
// locate the DOM element
var myVideo = document.getElementById('myVideo');

// create a VisSense instance with our video
var videoElementArea = VisSense(myVideo);

// create a monitor builder with the VisSense object
var monitorBuilder = VisSense.VisMon.Builder(videoElementArea);

// register a function that is called when the element becomes fully visible
monitorBuilder.on('fullyvisible', function() {
    myVideo.play(); // start playing the video (or keep playing)
});

// register a function that is called when the element becomes hidden
monitorBuilder.on('hidden', function() {
    myVideo.pause(); // pause the video (or stay paused)
});

// finish the builder an make a concrete monitor
var videoVisibilityMonitor = monitorBuilder.build();

// start observing the element
videoVisibilityMonitor.start();
```

Fine, that's great! But what if we want the video to start playing when - let's say - three quarters are visible?
Instead of registering a 'percentage change' handler with some logic (which is one way to achieve it)
we just declare the element to be fully visible when 75% of it is visible:

```js
var myVideo = document.getElementById('myVideo');

VisSense.VisMon.Builder(VisSense(myVideo, {
    fullyvisible: 0.75
}))
.on('fullyvisible', function() {
    myVideo.play();
})
.on('hidden', function() {
    myVideo.pause();
})
.build()
.start();
```

See this example live and [try it on jsbin.com](https://jsbin.com/maqaco/edit?js,output).

Protip: if you ever want a monitor to stop observing the element you simply invoke the `stop()` method.

```js
VisSense.VisMon.Builder(VisSense(myVideo))
.on('start', function(monitor) {
  // stop observing after 60 seconds
  setTimeout(function() {
      monitor.stop();
  }, 60 * 1000);
})
.on('...', function() {
  // ...
})
.build()
.start();
```
