# ODS Stateless Component Development Details

Building the JavaScript and CSS for an Orion custom element requires a handful of processing events in order to produce the desired code needed per component that meets the needs of the current state of [browser support](https://github.com/AlaskaAirlines/OrionStatelessComponents__docs/blob/master/docs/BABEL_SUPPORT.md).

## Polymer Development

Developing and rendering components require Polymer resources. In order to easily support this in a development environment it is suggested that developers install the Polymer-CLI globally for dev use.

| Dependency | info |
|----|----|
| Polymer-CLI | `$ npm i polymer-cli -g`

To start a local component server:

```
$ polymer serve
```

## Custom fonts

Building components requires local access to custom web fonts. After installing the [Orion Web Core Stylesheet(OWCSS)](https://github.com/AlaskaAirlines/OrionWebCoreStyleSheets) project, see the docs for more information about how to access and render Orion's custom fonts.

## Building resources from Orion Design Tokens

The use of ODS components requires the use of **Token CSS Custom Properties** and **Token Sass Variables** from the [ODS Design Tokens](https://www.npmjs.com/package/@alaskaairux/orion-design-tokens) project.

This is necessary as each component references these global Custom Properties directly and many of the features of OWCSS require information from the Sass variables. When the Orion Design Tokens are updated, these values will influence the nested Web Components within the scope of the project as well as any project scoped Sass.

This process is represented in the `demo/` section of any custom element project.

### Style Dictionary scripts and config settings

Building out Sass Variables and CSS Custom Properties from Design Token JSON files is a key dependency for any CSS development. 

| Command | Description |
|----|----|
| `$ npm run buildTokens` | References JSON files within project and transpiles into CSS/Sass resources per the config file*† |

\* Each JSON file must have an individual config for individual resource building.

† Function is included as part of the `gulp build` and `gulp watch` processes.

| Dependency | Info | Project |
|---|---|---|
| Orion Design Tokens | `npm i @alaskaairux/orion-design-tokens` | [npm](https://www.npmjs.com/package/@alaskaairux/orion-design-tokens) |
| Style Dictionary | `npm i style-dictionary` | [npm](https://www.npmjs.com/package/style-dictionary) |

## Component CSS

[litElement](https://lit-element.polymer-project.org/) components are JavaScript modules that produce HTML custom elements. A feature of custom elements is encapsulated CSS through the use of the [shadowDOM](https://developers.google.com/web/fundamentals/web-components/shadowdom). Meaning, CSS needs to be written directly into the module itself.

Using [Sass](https://sass-lang.com/) and other techniques makes this undesirable to edit directly within the scope of the component JS file. To assist with this, the following script will process CSS resources into a JavaScript module that can be imported into the component.

| Dependency | Info | Project |
|---|---|---|
| WC Sass Render | `npm i wc-sass-render` | [npm](https://www.npmjs.com/package/wc-sass-render) |

| Command | Description |
|----|----|
| `$ npm run sassRender` | Converts CSS or Sass to JavaScript module |


## Accessibility(a11y) testing

The evaluation of a11y is a per-component responsibility. To test a11y performance, please see the [accessibility and testing](https://github.com/AlaskaAirlines/OrionStatelessComponents__docs/blob/master/docs/A11Y.md) documentation. 

## Development, what goes where?

The following details what type of code should go where within the scope of a custom element project. 

```
ODS-WC-Generator/template
├── LICENSE
├── NOTICE
├── README.md
├── demo
|  ├── alert.js
|  ├── index.html
|  └── sass
|     └── style.scss
├── gulpfile.js
├── index.html
├── package.temp
├── polymer.json
├── scripts
|  ├── componentConfig.json
|  ├── componentConfigDist.json
|  ├── tokenConfig.json
|  ├── tokenScript.js
|  └── tokenScriptCustom.js
├── src
|  ├── ods-[name].js
|  ├── shape.json
|  └── style.scss
└── test
   ├── index.html
   └── ods-[name]_test.html
```

**./demo**: The purpose of this directory is to produce a demo page for development and review. Updates would include editing the `./demo/index.html` and `./demo/sass/style.scss` documents.

**./docs**: If there are additional documents per your new custom element, please place all Markdown files in the `./docs` directory.

**./scripts**: This directory is NOT to be used for any component specific code. This directory is specifically for the Polymer Development environment only.

**./src**: Your new Orion Custom Element will be developed inside a Polymer Development Environment, so all the code that pertains specifically to your new web component will live in the `./src` directory. Javascript, JSON and Sass will all need to be placed ONLY in the `./src` directory. If placed anywhere else, this will cause issues with the packing process.

## Your 1st commit

With the current configurations, when committing code to a new repo, Githooks should be working. To validate, when committing code a series of pre-commit tests should run. To validate, run the following commands:

```bash
$ git add .
$ git commit -m "chore: initial commit from generator"
```

In your Git logs you should see the following line output:

```bash
husky > commit-msg (node v10.16.3)
```

If you do not, then the pre-commit hooks are **not working**. To fix, delete `package-lock.json`, and the `node_modules` directory, then re-install all packages.


## Component Demo

For the purpose of demonstrating an element or component the demo requires all the same dependencies that other projects do. This includes Design Tokens, OWCSS breakpoints; fonts; normalize; baseline and utility classes.

Having these resources as dependencies allows for independent development and release cycles between dependencies and individual components.

The best way to address this within demos per element or component is to have a `style.scss` file in the `demo/` directory that will process all the necessary dependencies into usable CSS at the page level.

OWCSS resources have a dependency on Sass variables while components use [CSS custom properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties). It is important to have both these files generated and used in a project.


## Iron icons for demo/index.html

`iron-icons` is a Polymer utility that includes definition for the `iron-iconset-svg` element, as well as an import for the default icon set.

Icon icons are **not used** for Orion purposes. This is a utility only used for the purposes of the **demo** within each component directory.

See [demo](https://www.webcomponents.org/element/@polymer/iron-icons/demo/demo/index.html)

##
<footer>
<img src="https://resource.alaskaair.net/-/media/2C1969F8FB244C919205CD48429C13AC" alt="Orion Design System Logo" title="Be the change you want to see" width="50" align="right" />
Alaska Airlines Orion Design System<br>
Copyright 2019 Alaska Airlines, Inc. or its affiliates. All Rights Reserved.
</footer>
