# Babel Support

The use of modern HTML custom elements and leveraging supporting libraries like LitElement requires developers employ modern coding techniques. This is especially crucial with the use of ES6+ JavaScript. As a result, older browsers still in use that do not support ES6+ will not  support rendering of HTML custom elements. 

To address this, Alaska Airlines developers are encouraged to use Babel to transpile ES6+ code to whatever legacy version of ECMAScript is needed to meet their support matrix. 

The following is an example of how to configure Babel that best meets the current deliverable support standard. 

## Configuring Babel

The following is an example of a Babel config:

```javascript
/* .babelrc.js */

module.exports = {
  presets: [
    [
      '@babel/preset-env',
      {
        useBuiltIns: 'usage', // automatically import polyfills when needed based on "unsupported" feature usage
        corejs: '3.0.0',
        targets: {
          chrome: '70',
          edge: '40',
          ie: '10',
          safari: '9',
          firefox: '63',
          ios: '11',
          android: '7',
        },
      },
    ],
    // include other presets here (e.g. @babel/preset-react)
  ],
  plugins: [
    '@babel/plugin-proposal-class-properties', // optional, but nice for making JS classes look *more* like Java or C# classes
    '@babel/plugin-transform-spread', // support ES6 spread operators in older browsers (e.g. [ ...subset1, ...subset2 ])
    [
      '@babel/plugin-proposal-object-rest-spread', // support ES6 object spread operators in older browsers (e.g. { ...object1, ...object2 })
      {
        useBuiltIns: true,
      },
    ]
    '@babel/plugin-transform-template-literals', // suport ES6 string template literals in older browsers (e.g. `Hello, ${nameVariable}!`)
  ],
  env: {
    test: {
      plugins: [
        '@babel/plugin-transform-modules-commonjs' // transform `import x from 'y'` syntax to `const x = require('y')` in test environment
        ],
    },
  },
};
```

For the above babel config, run the following npm install command:

```shell
npm i -D @babel/core @babel/polyfill @babel/preset-env @babel/plugin-proposal-class-properties @babel/plugin-proposal-object-rest-spread @babel/plugin-transform-modules-commonjs @babel/plugin-transform-spread @babel/plugin-transform-template-literals core-js@3
```

This might look like a lot, keep in mind you are not adding the full weight of each of these to your final build. You're only using most of these to transform some normal JS code into JS code that is recognized by legacy browsers.

That being said, your build size _will_ increase significantly, and your performance will _likely_ drop as well, due to ES6 efficiencies lost by compiling down to ES5.

## Configuring Webpack

With Webpack, projects can use a more modern module import syntax complete with built-in tree shaking, as well as a whole host of other pre-compiled web technology.

The following is a stripped down example of a webpack config that will utilize our `.babelrc.js` from above to add browser support to our bundled JS build output.

```javascript
/* webpack.config.js */

module.exports = {
  // ...

  devtool: "source-map",

  module: {
    rules: [
      {
        test: /\.js/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      }

      // ...
    ]
  }
};
```

### Packages without legacy browser support

Many packages do not meet the specifications of Alaska's legacy browser support, mainly due to use of modern code. These will include internal and external packages. 

To address packages without built-in legacy browser support, please do the following within the webpack config rule for babel:

```javascript
/* webpack.config.js */
const path = require("path");

module.exports = {
  // ...

  module: {
    rules: [
      {
        test: /\.js/,
        include: [
          // list all locations that need to be babelized for browser support
          path.resolve(__dirname, "src"),
          path.resolve(__dirname, "node_modules/lit-element"),
          path.resolve(__dirname, "node_modules/lit-html"),
          path.resolve(__dirname, "node_modules/@alaskaairux/ods-button"),
          path.resolve(__dirname, "node_modules/@alaskaair/app-insights-logger"),
          path.resolve(__dirname, "node_modules/react-map-gl")
        ],
        use: {
          loader: "babel-loader"
        }
      }

      // ...
    ]
  }
};
```

##

<footer>
<img src="https://resource.alaskaair.net/-/media/2C1969F8FB244C919205CD48429C13AC" alt="Orion Design System Logo" title="Be the change you want to see" width="50" align="right" />
Alaska Airlines Orion Design System<br>
Copyright 2019 Alaska Airlines, Inc. or its affiliates. All Rights Reserved.
</footer>

