# Creating a custom preset

You can now create a script with your own preset to use in your website or for distributing it to others. All you have to do is give it a name and set all the options you need it to load correctly. Remember to not import all config, properties not needed can be omitted.

Publish your preset with `tsparticles-preset` tag on `NPM` so everyone can find it.

You'll find a sample below.

## Fire preset sample

_fire.preset.js_ - The custom preset script, you can distribute it or reuse in all your websites.

```javascript
// call this method before initializing tsParticles, this preset will be available in all of your tsParticles instances
// parameters: preset name, preset partial options
tsParticles.addPreset("fire", {
  fpsLimit: 40,
  particles: {
    number: {
      value: 80,
      density: {
        enable: true,
        value_area: 800
      }
    },
    color: {
      value: ["#fdcf58", "#757676", "#f27d0c", "#800909", "#f07f13"]
    },
    opacity: {
      value: 0.5,
      random: true
    },
    size: {
      value: 3,
      random: true
    },
    move: {
      enable: true,
      speed: 6,
      random: false
    }
  },
  interactivity: {
    events: {
      onclick: {
        enable: true,
        mode: "push"
      },
      resize: true
    }
  },
  background: {
    image: "radial-gradient(#4a0000, #000)"
  }
});
```

_config.json_ - The config section to add to your config or in your plugin readme to teach others on how to use it.

```javascript
{
  "preset": "fire" // this should match the name above, it can be used in array values too, it will be loaded in order like everyone else
}
```
