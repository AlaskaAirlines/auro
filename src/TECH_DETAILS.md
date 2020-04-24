# Auro Web Component Development Details

Building the JavaScript and CSS for an Auro custom element requires a handful of processing events in order to produce the desired code needed per component that meets the needs of the current state of [browser support](https://github.com/AlaskaAirlines/OrionStatelessComponents__docs/blob/master/src/BROWSER_SUPPORT.md).

## Polymer Development

Current development and rendering demo components require Polymer resources. In order to easily support this in a development environment it is suggested that developers install the Polymer-CLI globally for dev use.

| Dependency | info |
|----|----|
| Polymer-CLI | `$ npm i polymer-cli -g`

To start a local component server:

```
$ polymer serve
```

## Custom fonts

Building components requires local access to custom web fonts. After installing the [Web Core Stylesheet(WCSS)](https://github.com/AlaskaAirlines/OrionWebCoreStyleSheets) project, see the docs for more information about how to access and render Auro's custom fonts.

## Building resources from Auro Design Tokens

The use of Auro components requires the use of **Token CSS Custom Properties** and **Token Sass Variables** from the [Auro Design Tokens](https://www.npmjs.com/package/@alaskaairux/orion-design-tokens) project.

## Component CSS

[litElement](https://lit-element.polymer-project.org/) components are JavaScript modules that produce HTML custom elements. A feature of custom elements is encapsulated CSS through the use of the [shadowDOM](https://developers.google.com/web/fundamentals/web-components/shadowdom). Meaning, CSS needs to be written directly into the module itself.

Using [Sass](https://sass-lang.com/) and other techniques is preferred versus editing CSS directly within the scope of the component JS file. To assist with this, the following script will process CSS resources into a JavaScript module that can be imported into the component.

| Dependency | Info | Project |
|---|---|---|
| WC Sass Render | `npm i wc-sass-render` | [npm](https://www.npmjs.com/package/wc-sass-render) |

## Accessibility(a11y) testing

The evaluation of a11y is a per-component responsibility. To test a11y performance, please see the [accessibility and testing](https://github.com/AlaskaAirlines/OrionStatelessComponents__docs/blob/master/src/A11Y.md) documentation.

## Automated unit testing

Automated unit tested is baked into each new component from the WC-Generator. For more information as to the technical details, please see [the docs](https://github.com/AlaskaAirlines/OrionStatelessComponents__docs/blob/master/src/TESTS.md).

## Development, what goes where?

The following details what type of code should go where within the scope of a custom element project.

```
WC-Generator/template
├── LICENSE
├── NOTICE
├── README.md
├── demo
|  ├── alert.js
|  ├── index.html
|  └── sass
|     └── style.scss
├── docs
|  └── index.html
├── index.html
├── index.js
├── karma.conf.js
├── package.temp
├── packageScripts
|  └── postinstall.js
├── polymer.json
├── scripts
|  ├── polyfills.js
|  ├── postCss.js
|  └── postinstall.js
├── src
|  ├── [namespace]-[name].js
|  └── style.scss
└── test
   └── [namespace]-[name].test.js
```

**./demo**: The purpose of this directory is to produce a demo page for development and review. Updates would include editing the `./demo/index.html` and `./demo/sass/style.scss` documents.

**./docs**: The `index.html` in this directory is pre-configured to be a pre-bundled asset demo page. See below for more instructions. 

**./packageScripts**: If there are scripts that needs to ship with the component, place them here and configure the `distJS` script to copy over any needed assets. 

**./scripts**: This directory is NOT to be used for any component specific code. This directory is specifically for the local development environment only.

**./src**: Your new web component will be developed inside a Polymer Development Environment, so all the code that pertains specifically to your new web component will live in the `./src` directory. Javascript, JSON and Sass will all need to be placed ONLY in the `./src` directory. If placed anywhere else, this will cause issues with the packing process.

**./test**: Location for all component related test files.


## Polymer Component Demo

For the purpose of demonstrating an element or component the demo requires all the same dependencies that other projects do. This includes Design Tokens, WCSS breakpoints; fonts; normalize; essential and utility classes.

Having these resources as dependencies allows for independent development and release cycles between dependencies and individual components.

The best way to address this within demos per element or component is to have a `style.scss` file in the `demo/` directory that will process all the necessary dependencies into usable CSS at the page level.

WCSS resources have a dependency on Sass variables while components use [CSS custom properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties). It is important to have both these files generated and used in a project.

## Pre-compiled demo

Part of the WC build system is creating pre-bundled assets that are IE11 compatible. To run the view for this, run the server command, 

```
$ npm run bundle:test
```

This will bundle the component and it's dependencies and start a server on `localhost:3000`. The code for this view is located in `./docs/index.html`. 

With the initial generation of assets, this template view will contain the following code. 

The stylesheet links will be updates with the most recent versions of Design Tokens and WCSS. 

```html
<div id="assets">
  <link rel="stylesheet" href="https://unpkg.com/@alaskaairux/orion-design-tokens@[designTokens]/dist/tokens/CSSCustomProperties.css" />
  <link rel="stylesheet" href="https://unpkg.com/@alaskaairux/orion-web-core-style-sheets@[wcss]/dist/bundled/essentials.css" />

  <!-- for initial build and test only -->
  <script src="../dist/polyfills.js"></script>
  <script src="../dist/[namespace]-[name]__bundled.js"></script>

  <!-- once first build has been released, update with the links below -->
  <!-- Be sure to update the :version number -->
  <!-- <script src="https://unpkg.com/@alaskaairux/[namespace]-[name]@:version/dist/polyfills.js"></script>
  <script src="https://unpkg.com/@alaskaairux/[namespace]-[name]@:version/dist/[namespace]-[name]__bundled.js"></script> -->
</div>
```

Once the new WC is ready for distribution, the code that is referencing the local polyfill and bundled JS should be updated with the lines that are commented out. 

These lines will be updated with the namespace and name of the new component, but the `:version` will need to be updated with the new WC version number. 

With this in place and referencing published assets, the Github repo can be configured to use the `./docs.index.html` file for a `https://alaskaairlines.github.io/` page. 

## Iron icons for demo/index.html

`iron-icons` is a Polymer utility that includes definition for the `iron-iconset-svg` element, as well as an import for the default icon set.

Icon icons are **not used** for Auro purposes. This is a utility only used for the purposes of the **demo** within each component directory.

See [demo](https://www.webcomponents.org/element/@polymer/iron-icons/demo/demo/index.html)
