# ODS Stateless Components

Orion Design System Stateless Components are framework agnostic reusable HTML custom elements intended for use across all internal and external facing applications across all of IT and e-commerce at Alaska Airlines.

Contained within individual repositories will be the resources needed to build and deploy individual components and elements as they pertain to the Orion Design System (ODS)

Please see all other documentation in regards to `CONTRIBUTING`, `CODE_OF_CONDUCT` and software `LICENSE` agreements of use.

## Element or Component?

The difference between an element or a component is mainly for semantics and reference. Regardless of naming, there is no difference in development.

* **BASE Custom Element**: Stand-alone UI that is unable to individually complete a task. E.g. a button. Alone a button cannot complete a task unless it is associated with another context.
* **Component**: UI that is comprised of two or more elements and is able to individually complete a task. E.g. a button and a text element in conjunction would make a component.

## Install development resources

For install and setup instructions, please see [PROJECT_SETUP](/docs/PROJECT_SETUP.md) and [TECH_DETAILS](docs/TECH_DETAILS.md) documents within this repository.

## Component directory structure

The following boilerplate directory structure will be found in the [ods-wc-generator](https://github.com/AlaskaAirlines/ODS-WC-Generator) project. Be sure to read all the setup instructions in README.md prior to any development.

```
/ODS-WC-Generator/template
├── LICENSE
├── NOTICE
├── README.md
├── demo
|  ├── alert.js
|  ├── index.html
|  └── sass
|     └── style.scss
├── docs
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

## What defines the shape of a element or component?

One of the main goals of the ODS Stateless Components project is to not only produce reusable UI components to be used in the web space, but to also define the shape of the component in a way that this information is useful to other platforms.

Within the `./src/` directory for each component there will be a `shape.json` file. It is the intent of this file to describe the shape of the component and in turn it will define the variables to be used when building the Sass for the component itself.

Please refer to all notes and examples contained within this file for any questions.

```
/OrionStatelessComponents
├── src
|  └── shape.json
```



##

<img src="https://resource.alaskaair.net/-/media/2C1969F8FB244C919205CD48429C13AC" alt="Orion Design System Logo" title="Be the change you want to see" width="50" align="right" />
Alaska Airlines Orion Design System<br>
Copyright 2019 Alaska Airlines, Inc. or its affiliates. All Rights Reserved.

