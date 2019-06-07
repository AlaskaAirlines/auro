# Web Component Polyfill Support

Polymer Web Components and lit-element are not supported by legacy browsers, especially anything in the IE family of browsers.

The Orion Web Components take a two-step process to support legacy browsers.

1. Each component package comes with CSS fallbacks
2. The project needs to test for Web Component support and apply the appropriate polyfills

In regards to the polyfills, Polymer, and by extension lit-element, addresses many of these issues. But there are a few additional polyfills needed based on the browser.

The best way to address this is by one of the following.

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


##

<img src="https://resource.alaskaair.net/-/media/2C1969F8FB244C919205CD48429C13AC" alt="Orion Design System Logo" title="Be the change you want to see" width="50" align="right" />
Alaska Airlines Orion Design System<br>
Copyright 2019 Alaska Airlines, Inc. or its affiliates. All Rights Reserved.
