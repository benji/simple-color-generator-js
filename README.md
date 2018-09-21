## SimpleColorGenerator

A simple JS library for quickly get a decent array of colors.

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
});

var borderColors = gen.getColors({
  saturation: "50%",
  lightness: "50%",
  alpha: 1
});
```

### Options

**SimpleColorGenerator() options:**

| Name      | Default                                 | Description                                                           |
| --------- | --------------------------------------- | --------------------------------------------------------------------- |
| count     | 10                                      | Number of colors to generate.                                         |
| seed      | Math.random() (no seed)                 | A float between 0 and 1. If set, will always produce the same colors. |
| randomize | true if no seed is set, false otherwise | Shuffles the colors.                                                  |

**getColors() options:**

| Name       | Default | Description        |
| ---------- | ------- | ------------------ |
| saturation | "50%"   | Saturation to use. |
| lightness  | "50%"   | Lightness to use.  |
| alpha      | 1.      | Alpha to use.      |

### License

[Apache License 2.0](LICENSE)
