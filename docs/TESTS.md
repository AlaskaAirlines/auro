# Running Tests

The native Polymer Test scenario depends on Selenium server for local browsers and Java installed. Due to complexities with getting these environments configured correctly, these rarely work and it is suggested to use the simpler interactive test method as described below.

#### Run the Polymer Server

```
$ polymer serve
```

#### Visit the following URL:

```
http://127.0.0.1:8081/components/@alaskaair/ods-[name]/test/ods-[name]_test.html
```

Open the inspector/console to review results of the tests.


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
