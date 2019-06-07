# Orion Stateless Component Browser Support

The Orion Stateless component developed per this repository is compliant with Alaska Airlines' browser support matrix as published at the time of this project's publication. 

If at any such time it is discovered that there is an issue with this component's support of any popular browser in use, please submit an issue and explain the discovered issue to the best of your ability. 

## Browser Support Matrix

Alaska Airlines currently supports the following browsers for the delivery of Stateless Web Components.

<small>Browsers that engineers are required to dev and test against:</small>

| Browser | Version | Operating System |
|------|------|------|
| Chrome | Current release | Windows, macOS, iOS, Android |
| Safari | Current release | macOS, iOS |
| Firefox | Current release | Windows, macOS, Android |
| Edge* | Current release | Windows 10 |
| Internet Explorer | 11 | Windows 7, Windows 8, Windows 10 |
| Internet Explorer | 10 | Windows 7, Windows 8 |

\* Edge currently refers to the original Microsoft version of the browser using the EdgeHTML engine. There is no official support for the upcoming Edge Chromium browser for macOS or Windows.

#### Browser support for HTML Web Components

| Feature | Chrome | Opera | Safari | Firefox | Edge | IE
|----|----|----|----|----|----|----|
| HTML Templates | Stable | Stable | Stable | Stable | Stable | Transpiling†/Polyfill* |
| Custom Elements | Stable | Stable | Stable | Stable | Polyfill | Transpiling†/Polyfill* |
| Shadow DOM | Stable | Stable | Stable | Stable | Polyfill | Transpiling†/Polyfill* |
| ES Modules | Stable | Stable | Stable | Stable | Stable | Transpiling†/Polyfill* |

[webcomponents.org](https://www.webcomponents.org/)

† Transpiling from ES6 to ES5 is required for browser support. See [Babel Support doc](/docs/BABEL_SUPPORT.md) for information about Babel configuration support options.

\* JavaScript polyfills are required in order for these browsers to render Polymer/Lit-element web components. See the [polyfill doc](/docs/POLYFILL.md) for more information on installment options.  

#### Browser support for CSS Custom Properties (variables)

| Browser | Version | Custom Selectors |
|------|------|------|
| Chrome | Current release | Yes |
| Safari | Current release | Yes |
| Firefox | Current release | Yes |
| Edge | Current release | Yes |
| Internet Explorer | 11 | No* |
| Internet Explorer | 10 | No* |

\* Fallback CSS is required to support browser. See [Custom Properties doc](/docs/CUSTOM_PROPERTIES.md) for information about setup and configuration.


##

<img src="https://resource.alaskaair.net/-/media/2C1969F8FB244C919205CD48429C13AC" alt="Orion Design System Logo" title="Be the change you want to see" width="50" align="right" />
Alaska Airlines Orion Design System<br>
Copyright 2019 Alaska Airlines, Inc. or its affiliates. All Rights Reserved.
