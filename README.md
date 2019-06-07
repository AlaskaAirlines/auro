<img src="https://resource.alaskaair.net/-/media/2C1969F8FB244C919205CD48429C13AC" alt="Orion Design System Logo" title="Be the change you want to see" width="125" align="right" />

[![Build Status](https://travis-ci.org/AlaskaAirlines/OrionStatelessComponents__docs.svg?branch=master)](https://travis-ci.org/AlaskaAirlines/OrionStatelessComponents__docs)
![npm (scoped)](https://img.shields.io/npm/v/@alaskaairux/docs.svg?color=orange)
![NPM](https://img.shields.io/npm/l/@alaskaairux/docs.svg?color=blue)

# Orion Stateless Components Standard Docs

All information regarding Project Setup, Technical Details, Tests and information regarding ODS Stateless Components can be found in the [./docs](/docs/) directory of this repository.

# Design Token CSS Custom Property dependency

The use of any ODS Component has a dependency on the [ODS Design Tokens](https://www.npmjs.com/package/@alaskaairux/orion-design-tokens). See repository and API information [here](https://github.com/AlaskaAirlines/OrionDesignTokens).

For additional details in regards to using Orion Design Tokens with components, please see [./docs/TECH_DETAILS.md](/docs/TECH_DETAILS.md)

# CSS Custom Property fallbacks

In older browsers where CSS Custom Properties are not supported, fallback properties are pre-generated and included with the npm. Any update to the Orion Design Tokens will be immediately reflected with supporting browsers. Legacy browsers will need updated components with pre-generated fallback properties.

# Alternate Orion Design Token build solutions

Included with a distributed npm are two additional directories, `./altImports/canonical` and `./altImports/variable`.

| directory | description |
|---|---|
| altImportsCanonical† | Sass using canonical values within the scope of the file |
| altImportsVariable* | Sass using CSS Custom Properties within the scope of the file |

† Using canonical CSS properties breaks inheritance chain from Orion Design Tokens

\* Orion Design Tokens are required to import any file using CSS Custom Properties. Also see Orion Design Tokens [pre-processed resources](https://github.com/AlaskaAirlines/OrionDesignTokens#install-pre-processed-resources). PostCSS using `postcss-custom-properties` will need to be added to your project if you are supporting legacy browsers.

```bash
├── altImports
|  ├── canonical
|  |  ├── style.css
|  |  └── style_clean.scss
|  └── variable
|     ├── style.css
|     └── style_clean.scss
```

It is highly recommended that you import the `style_clean.scss` this into a name-space as not to create style collisions. For example:

```scss
.ods-[name] {
  @import "./node_modules/@alaskaairux/ods-[name]/altImports/variable/style_clean.scss";
}
```

This pattern will produce all the selectors within `style_clean.scss` with the prefixed selector.

```scss
.ods-[name] .[name] {
  display: var(--ods-[name]-display);
  font-family: var(--ods-[name]-font-family);
  border-width: var(--ods-[name]-border-width);
  border-radius: var(--ods-[name]-border-radius);
  ...
}
```

**Warning!** Using the canonical CSS will break the chain of using Design Tokens. If Tokens are updated, this will require the update of the components and their canonical output. Use with caution.
