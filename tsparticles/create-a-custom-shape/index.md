# Creating a custom shape for tsParticles

You can now create a script with your own shape to use in your website or for distributing it to others. All you have to do is a drawing function, give it a name and use it in the config.

Publish your shapes with `tsparticles-shape` tag on `NPM` so everyone can find it.

You'll find a sample below.

## Spiral sample

_spiral.js_ - The custom shape script, you can distribute it or reuse in all your websites.

```javascript
// call this method before initializing tsParticles, this shape will be available in all of your tsParticles instances
// parameters: shape name, drawing method
tsParticles.addCustomShape("spiral", function(context, particle, radius) {
  const shapeData = particle.shapeData;
  const realWidth = (radius - shapeData.innerRadius) / shapeData.lineSpacing;

  for (let i = 0; i < realWidth * 10; i++) {
    const angle = 0.1 * i;
    const x = (shapeData.innerRadius + shapeData.lineSpacing * angle) * Math.cos(angle);
    const y = (shapeData.innerRadius + shapeData.lineSpacing * angle) * Math.sin(angle);

    context.lineTo(x, y);
  }
});
```

If you prefere using classes you can, `IShapeDrawer` interface can be implemented in your code or at least a class with a method `draw(context, particle, radius)` in it. You can find a sample below.

```javascript
class SpiralDrawer {
  draw(context, particle, radius) {
    const shapeData = particle.shapeData;
    const realWidth = (radius - shapeData.innerRadius) / shapeData.lineSpacing;

    for (let i = 0; i < realWidth * 10; i++) {
      const angle = 0.1 * i;
      const x = (shapeData.innerRadius + shapeData.lineSpacing * angle) * Math.cos(angle);
      const y = (shapeData.innerRadius + shapeData.lineSpacing * angle) * Math.sin(angle);

      context.lineTo(x, y);
    }
  }
}

// call this method before initializing tsParticles, this shape will be available in all of your tsParticles instances
// parameters: shape name, drawer class
tsParticles.addCustomShape("spiral", new SpiralDrawer());
```

_config.json_ - The config section to add to your config or in your plugin readme to teach others on how to use it.

```javascript
{
  // [... omitted for brevity]
  "particles": {
    // [... omitted for brevity]
    "shape": {
      "type": "spiral", // this must match the name above, the type works as always, you can use an array with your custom shape inside
      "custom": {
        // this must match the name above, these are the values set in particle.shapeData (the first line of the method above)
        // you can use array as value here too, the values will be random picked, like in standard shapes
        "spiral": {
          "innerRadius": 1,
          "lineSpacing": 1,
          "close": false, // this value is used by tsParticles to close the path, if you don't want to close it set this value to false
          "fill": false // this value is used by tsParticles to fill the shape with the particles color, if you want only the stroke set this value to false
        }
      }
      // [... omitted for brevity]
    }
    // [... omitted for brevity]
  }
  // [... omitted for brevity]
}
```