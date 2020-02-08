# Custom Properties Support

CSS custom properties, aka CSS variables, are only supported by current browsers.

| Browser | Supported release | Release date | Engine |
|---|---|---|---|
| Chrome	| 49 | March 2, 2016 | Blink |
| Safari	| 9.1 | March 20, 2016 | Webkit |
| Firefox | 31 | July 21, 2014 | Gecko |
| Edge		| 16 | October 16, 2017 | EdgeHTML |
| Opera 	| 36 | March 6, 2016 | Blink |
| Internet Explorer | no support | no support | Trident |

As a result, when CSS custom properties are used, the use of fallback CSS is necessary to support legacy Internet Explorer users.

## How CSS Custom Properties Work

With supporting browsers, the following code example would render the appropriate color in the view.

```css
:root {
  --base-color: #222000;
}

.selector {
  color: var(--base-color);
}
```

In cases with custom elements that use the shadow DOM with encapsulated CSS support, custom properties can be written to the scope of the component. In this example, the `:host` selector would overwrite the `:root` selector and render the color red versus black.

```css
:host {
  --base-color: #ff000;
}

.selector {
  color: var(--base-color);
}
```

### Legacy browser support

Browsers work on the principal of progressive enhancement. This means that you can send code to the browser that it does not understand and it will simply ignore it. When using CSS custom properties, this means that the value will never be rendered to the view and your UI will appear broken.

The solution for this is to provide fall back properties like so:

```css
.selector {
  color: #ff000;
  color: var(--base-color);
}
```

With this code, any browser will see `color: #ff000;`. Those that understand `color: var(--base-color);` this property will override the previous. For those that do not understand this property, it will simply ignore.

### Fallback properties at scale

Producing fallback properties at scale require additional CSS processing. This and other projects use the PostCSS plugin of postcss-custom-properties. There are many framework dependent uses from Gulp to Webpack. The following is a Node version.

```javascript
/* ./scripts/postcss.js */

const postcss = require('postcss');
const postcssCustomProperties = require('postcss-custom-properties');
const fs = require('fs');

const startingCSS = './raw.css';
const finishCSS = './dist.css';

fs.readFile(startingCSS, (err, css) => {
  postcss([
    postcssCustomProperties ({ preserve: true }),
  ])
    .process(css, { from: startingCSS, to: finishCSS })
    .then(result => {
      fs.writeFile(finishCSS, result.css, () => true)
    })
})
```

Using this script, the following CSS ...

```css
:root {
  --base-color: #222000;
}

.selector {
  color: var(--base-color);
}
```

will output the following:

```css
:root {
    --base-color: #222000;
}

.selector {
  color: #222000;
  color: var(--base-color);
}
```
