# Web Component Polyfill Support

![npm (scoped)](https://img.shields.io/npm/v/@alaskaairux/ods-docs.svg?color=orange)

HTML custom elements and and litElement are not supported by legacy browsers, especially anything in the IE family of browsers.

The Auro Web Components take a two-step process to support legacy browsers.

1. Each component package comes with CSS fallbacks
2. The project needs to test for custom element support and apply the appropriate polyfills

A way to address this is by one of the following.

1. Load the `webcomponents-loader.js` via CDN
2. Load the `webcomponents-loader.js` internally with the project

### Load via CDN

In the head of your project, insert the following HTML*

```
<script src="https://cdnjs.cloudflare.com/ajax/libs/webcomponentsjs/x.x.x/webcomponents-loader.js"></script>
```

\* See [cdnjs.com](https://cdnjs.com/libraries/webcomponentsjs) for latest versions.

### Load with the project

#### Install

```
npm i @webcomponents/webcomponentsjs
```

#### Load Synchronous

Place the following script tag in the `<head>` of your main app template.

```
<script src="./node_modules/@webcomponents/webcomponentsjs/webcomponents-loader.js"></script>
```

Read more about the [npm package](https://www.npmjs.com/package/@webcomponents/webcomponentsjs) and the different ways to install as to best fit your needs.

### Option for React

With React there may be an issue with loading the `loader.js` file, so the follow code example may help.

```javascript
import ('@webcomponents/webcomponents.js').then(() => {
  import ('@alaskaairux/ods-button/dist/ods-button');
  import ('@alaskaairux/ods-hyperlink/dist/ods-hyperlink');
});
```


##
<footer>
Alaska Airlines Auro Design System<br>
Copyright 2019 Alaska Airlines, Inc. or its affiliates. All Rights Reserved.
</footer>
