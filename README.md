## SimpleColorGenerator

A simple JS library to quickly get a decent arrays of colors (hues) with different alpha/saturation/lightness components.

One example use case is creating colors that are plain for the border and slightly transparent or lighter for the background (see example below).

This is a 2 steps process:
1) Define how to produce the hues (how random and how many)
2) Generate different saturations, lightness and alpha variations for this palette.

![](https://raw.github.com/benji/simple-color-generator-js/master/samples.png)

---

Uses [HSLA](https://www.w3.org/wiki/CSS/Properties/color/HSLA) format.

### Usage

```javascript
var gen = SimpleColorGenerator({
  count: 10,
  seed: Math.random(),
  randomize: true
});

var bgColors = gen.getColors({
  saturation: "50%",
  lightness: "50%",
  alpha: 0.5
}); // => [ "hsla(11,50%,50%,0.5)", "hsla(191,50%,50%,0.5)", "hsla(83,50%,50%,0.5)", ... ]

// same hues with alpha=1
var borderColors = gen.getColors({
  saturation: "50%",
  lightness: "50%",
  alpha: 1
}); // => [ "hsla(11,50%,50%,1)", "hsla(191,50%,50%,1)", "hsla(83,50%,50%,1)", ... ]
```

### API 

**SimpleColorGenerator()**

| Option    | Default                                 | Description                                                           |
| --------- | --------------------------------------- | --------------------------------------------------------------------- |
| count     | 10                                      | Number of colors to generate.                                         |
| seed      | Math.random() (no seed)                 | A float between 0 and 1. If set, will always produce the same colors. |
| randomize | true if no seed is set, false otherwise | Shuffles the colors. see [predictable randomize](#predictable-randomize)                                                  |

**getColors()**

Returns an array of colors (String) in HSLA format based on the same hue values.

| Option     | Default | Description        |
| ---------- | ------- | ------------------ |
| saturation | "50%"   | Saturation to use. |
| lightness  | "50%"   | Lightness to use.  |
| alpha      | 1.      | Alpha to use.      |

### Predictable randomize

It's not possible out of the box since Javascript doesn't have a seed mechanism.

You can work around this by including [David Bau's excellent seedrandom library](https://github.com/davidbau/seedrandom) and setting the seed before calling SimpleColorGenerator:

```javascript
var hueSeed = .31
var randomizeSeed = "tulips"

Math.seedrandom(randomizeSeed);

var gen = SimpleColorGenerator({
  count: 10,
  seed: hueSeed,
  randomize: true
});
```

This will make sure you get the exact same array of colors every time, even afer a page refresh.

### NodeJS

```
npm install @benji/simple-color-generator@1.0.1
```

```
const SimpleColorGenerator = require('simple-color-generator') 
var gen = SimpleColorGenerator({ count: 10 });
var colors = gen.getColors({ alpha: 0.5 });
```

### License

[Apache License 2.0](LICENSE)
