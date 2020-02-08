# React Quickstart Setup

![npm (scoped)](https://img.shields.io/npm/v/@alaskaairux/ods-docs.svg?color=orange)

The purpose of this document is to illustrate a bootstrap environment using **Create-React-App** and all currently available Orion Design System resources.

## Create React App

Install create-react-app globally

```
$ npm i create-react-app -g
```

To start your own project, use create-react-app to bootstrap a new build

```
$ create-react-app my-project
```

Once the bootstrap app has been created, `cd/` in to the new project directory and start the server

```
$ npm start
```

## Design Tokens

Design Tokens are required to drive the overall UI of the Orion Design System. These set-up instructions will address installing tokens as native CSS custom properties.

```
$ npm i @alaskaairux/orion-design-tokens
```

Open `./src/index.js` and add the following line to the header of the document:

```Javascript
import "@alaskaairux/orion-design-tokens/dist/tokens/CSSTokenProperties.css";
```

This addition will add all the Orion Design Token CSS custom properties to your global CSS. To validate, run the application and view Elements/Styles within the Chrome Inspector.

### Building custom Token pipeline

If desired, [view documentation](https://github.com/AlaskaAirlines/OrionDesignTokens#build-orion-design-tokens-pipeline) for how to build your own custom pipeline when using Orion Design Tokens with Style Dictionary.

## Web Core Stylesheets

Orion Web Core Style sheets is a responsive, mobile-first collection of styles and tools designed to make it quick and simple for developers to create web experiences using the Orion Design Language.

This resource is built using Sass, so you will need to install Sass in your project.

```
$ npm i node-sass
```

**NOTE:** If you are setting up in a project where you have customized your WebPack configuration, you may need to install other resources to get Sass working.

When using Create React App, using Sass is pre-configured, so post the install of `node-sass`, the last step is to change the current files from `.css` to `.scss` and their relative references.

Install Orion Web Core Stylesheets

```javascript
$ npm i @alaskaairux/orion-web-core-style-sheets
```


### Global install of Sass resources

Given that `index.scss` is kind of the top-most resource always called into the app views, let's place our global Sass resources in that file.

At the top of the document, first point to the Sass version of the Orion Design Tokens:

```scss
@import '~@alaskaairux/orion-design-tokens/dist/tokens/TokenVariables';
```

Installing this resource allows for the use of Sass variables of the Orion Design Tokens.

Next, let's point to Orion Breakpoints:

```scss
@import "~@alaskaairux/orion-web-core-style-sheets/dist/breakpoints";
```

This is a functional utility file that lists all the different [pre-defined mobile-first breakpoints](https://alaskaairlines.github.io/OrionWebCoreStyleSheets/#responsive-mixin).

Next, let's install the `@font-face` styles.

```sass
@import "~@alaskaairux/orion-web-core-style-sheets/dist/fonts";
```

This file contains all the `@font` rules for using the approved Orion fonts.

Next, let's point to the normalize styles:

```scss
@import "~@alaskaairux/orion-web-core-style-sheets/dist/normalize";
```

This file sets a normalization across all browsers. It's like a reset, but not as harsh.

Last, point to the Orion Baseline file:

```sass
@import "~@alaskaairux/orion-web-core-style-sheets/dist/baseline";
```

The role of this file is to establish a shared baseline CSS between projects and browsers alike.

If interested, there is a growing standard of utility selectors that can be used with projects as well.

```scss
@import "~@alaskaair/orion-web-core-style-sheets/dist/utilityClasses";
```

[View here](https://alaskaairlines.github.io/OrionWebCoreStyleSheets/) to see the entire OWCSS API, including the various Utility Selectors currently available.


## Orion Icons

Orion Icons is a standard set of SVG icons that can be used with any web project. See the [icons reference](http://orion-design.surge.sh/#icons) for a visual grid of icons currently being used.

```javascript
$ npm i @alaskaairux/orion-icons
```

Post install, your project will need to subscribe to the Icon specific Design Tokens. To do this, you can either link to the CSS file that is contained within the distributed package:

```Javascript
import "@alaskaairux/orion-icons/dist/tokens/CSSTokenProperties.css";
```

Or you can import the Icon Token properties in your Sass setup:

```Sass
@import "~@alaskaairux/orion-icons/dist/tokens/TokenProperties"
```

All other use documentation can be found in the repository's [README](https://github.com/AlaskaAirlines/OrionIcons/blob/master/README.md) file.



## Install ODS Component

ODS Components are fully contained native [HTML Custom Elements](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_custom_elements). To start using components, let's look at the [\<ods-hyperlink>](https://github.com/AlaskaAirlines/OrionStatelessComponents__ods-hyperlink) component.

```
$ npm i @alaskaairux/ods-hyperlink
```

Update `./src/App.js` to make use of the dependency:

```js
import "@alaskaairux/ods-hyperlink/dist/ods-hyperlink";";
```

Then update the `App` component in the `./src/App.js` file:

```js
class App extends Component {
  render() {
    return (
      <div className="App">

        ...
        <ods-hyperlink href="https://reactjs.org" target="_blank">Learn React</ods-hyperlink>
        ...

      </div>
    );
  }
}
```

## Progressive Web App

It is highly suggested that all apps are setup to take advantage of the service worker architecture. To ensure that this new app is applicable to be a Progressive Web App, make this update in `./src/index.js`:

```
serviceWorker.unregister();

to

serviceWorker.register();
```

To test that this new service worker is indeed working, it is required to build the project as services workers do not work in the dev environment for various reasons.

Once am optimized build as been created, `cd/` into the `./build` directory and run any simple server to serve up the app. Keep in mind that service workers require a `https://` connection, but this does not apply to `localhost`.

Be sure to update `public/manifest.json` per the project as well.


## Legacy browser support

To support legacy browsers, please see Orion's documentation on building in [backwards compatibility polyfill solution](https://github.com/AlaskaAirlines/OrionStatelessComponents__docs/blob/master/docs/POLYFILL.md).

### Babel support

In conjunction with the polyfill solution, developers will need to consider [babel support](https://github.com/AlaskaAirlines/OrionStatelessComponents__docs/blob/master/docs/BABEL_SUPPORT.md) that also includes customization of your project's [Webpack](https://github.com/AlaskaAirlines/OrionStatelessComponents__docs/blob/master/docs/BABEL_SUPPORT.md#configuring-webpack) config.

##
<footer>
Alaska Airlines Auro Design System<br>
Copyright 2019 Alaska Airlines, Inc. or its affiliates. All Rights Reserved.
</footer>
