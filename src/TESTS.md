# Testing 

Components created using the [ODS-WC-Generator](https://github.com/AlaskaAirlines/ODS-WC-Generator) will be configured with testing tools based on [open-wc](https://open-wc.org/) recommendations.

## Testing tools

[open-wc testing](https://open-wc.org/testing/) provides packages that bundle a fully functional testing suite, configures defaults, and exposes testing utilities.

The following packages are included as dev dependencies by the ODS WC Generator:
* [@open-wc/testing](https://www.npmjs.com/package/@open-wc/testing)
* [@open-wc/testing-karma](@open-wc/testing-karma)

The above open-wc packages will install a set of libraries to enable testing, including:

* [Chai](https://www.chaijs.com/) - Library of BDD / TDD assertions
* [Chai A11y aXe](https://open-wc.org/testing/testing-chai-a11y-axe.html) - Chai assertions for accessibility testing
* [Mocha](https://mochajs.org/) - Test suite runner
* [Karma](https://karma-runner.github.io/latest/index.html) - Supports running tests in multiple browsers
* [Sinon](https://sinonjs.org/) - Test spies, stubs, and mocks

To learn more about these testing libraries, please visit their respective documentation and [open-wc testing](https://open-wc.org/testing/).

## Configuration

`karma.conf.js` contains the configuration used by Karma. Refer to the [Karma - Configuration File](http://karma-runner.github.io/4.0/config/configuration-file.html) documentation for the specific settings that can be used with Karma.

[@open-wc/testing-karma](https://open-wc.org/testing/testing-karma.html) provides default Karma configuration in [create-default-config.js](https://github.com/open-wc/open-wc/blob/master/packages/testing-karma/src/create-default-config.js). This will set the Istanbul Reporter *statements / branches / functions/ lines* [coverage](https://github.com/open-wc/open-wc/blob/master/packages/testing-karma/src/create-default-config.js#L93) to **80%**. ODS components require all coverage thresholds to be met before committing. 

# Running Tests
The `package.json` for generated ODS components have the following test commands in the scripts block:

```json
"scripts": {
    ...
    "test": "karma start --coverage",
    "test:watch": "karma start --single-run=false --auto-watch=true",
    ...
}
```

`npm test` will start Karma, run a single execution of the package's tests, and generate a coverage report.


```bash
$ npm test
...
> karma start --coverage
...
Finished in 0.154 secs / 0.074 secs @ 10:47:45 GMT-0800 (Pacific Standard Time)

SUMMARY:
√ 13 tests completed
TOTAL: 13 SUCCESS

=============================== Coverage summary ===============================
Statements   : 100% ( 38/38 )
Branches     : 100% ( 18/18 )
Functions    : 100% ( 14/14 )
Lines        : 100% ( 38/38 )
================================================================================
```

The full [Istanbul](https://istanbul.js.org/) coverage report is available in `./coverage/index.html` and can be viewed in the browser.

## Debugging tests

If you wish to debug your unit tests interactively, you may use developer tools in the browser.

### Debugging in the browser via developer tools

1. Run Karma via the command line  

    `npm run test:watch`

1. Open the Karma UI using the URL in the test logs. You may need to replace `0.0.0.0` with `localhost`.

    ```bash
    05 11 2019 11:44:54.024:INFO [karma-server]: Karma v4.4.1 server started at http://0.0.0.0:9876/
    ```

1. Open the developer tools in your browser. Under `sources` find your tests in the `base/test/` directory.

1. Set breakpoints in the test and re-run the unit test in the Karma UI.

## Linting tests

Within the build and dist scripts are embedded CSS and JSON linters. If you are interested in running these tests individually, they are:

```
$ npm run cssLint

$ npm run jsonLint
```

Their primary use is within the build/dist and pre-commit scripts to ensure that the coded files are correct at the time of build.

##

<footer>
<img src="https://resource.alaskaair.net/-/media/2C1969F8FB244C919205CD48429C13AC" alt="Orion Design System Logo" title="Be the change you want to see" width="50" align="right" />
Alaska Airlines Orion Design System<br>
Copyright 2019 Alaska Airlines, Inc. or its affiliates. All Rights Reserved.
</footer>
