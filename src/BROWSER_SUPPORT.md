# Auro Web Component Browser Support

Auro Web components are developed to be compliant with Alaska Airlines' browser support matrix as published at the time of this project's publication.

If at any such time it is discovered that there is an issue with this component's support of any popular browser in use, please submit an issue and explain the discovered issue to the best of your ability.

## Browser Support Matrix

Alaska Airlines currently supports the following browsers for the delivery of stateless web components.

<small>Browsers that engineers are required to dev and test against:</small>

| Browser | Version | Operating System |
|------|------|------|
| Chrome | Current release | Windows, macOS, iOS, Android |
| Safari | Current release | macOS, iOS |
| Firefox | Current release | Windows, macOS, Android |
| Edge*† | Stable release | Windows 7, Windows 8, Windows 10 |
| Internet Explorer | 11 | Windows 7, Windows 8, Windows 10 |

\* The new Microsoft Edge is based on Chromium and was released on January 15, 2020. It is compatible with all supported versions of Windows, and macOS. Downloading the browser will replace the legacy version of Microsoft Edge  on Windows 10 PCs.

† Edge 18 is the final version to support [EdgeHTML](https://en.wikipedia.org/wiki/EdgeHTML) on Windows 10 machines only. There is no directive to individually support this version of Edge.

#### Browser support for HTML Web Components

| Feature | Chrome | Opera | Safari | Firefox | MS Edge (Chrome) | IE
|----|----|----|----|----|----|----|----|
| HTML Templates | Stable | Stable | Stable | Stable | Stable | Transpiling†/Polyfill* |
| Custom Elements | Stable | Stable | Stable | Stable | Stable†† | Transpiling†/Polyfill* |
| Shadow DOM | Stable | Stable | Stable | Stable | Stable†† | Transpiling†/Polyfill* |
| ES Modules | Stable | Stable | Stable | Stable | Stable | Transpiling†/Polyfill* |

[webcomponents.org](https://www.webcomponents.org/)

† Transpiling from ES6 to ES5 is required for browser support. See [Babel Support doc](https://github.com/AlaskaAirlines/auro_docs/blob/master/src/BABEL_SUPPORT.md) for information about Babel configuration support options.

†† This document only considers Microsoft Edge v79 and up. Legacy Edge versions on edgeHTML still requires full polyfill support.

\* JavaScript polyfills are required in order for these browsers to render Polymer/Lit-element web components. See the [polyfill doc](https://github.com/AlaskaAirlines/auro_docs/blob/master/src/POLYFILL.md) for more information on installment options.

#### Browser support for CSS Custom Properties (variables)

| Browser | Version | Custom Selectors |
|------|------|------|
| Chrome | Current release | Yes |
| Safari | Current release | Yes |
| Firefox | Current release | Yes |
| Edge | Current release | Yes |
| Internet Explorer | 11 | No* |

\* Fallback CSS is required to support browser. See [Custom Properties doc](https://auro.alaskaair.com/support/custom-properties) for information about setup and configuration.

