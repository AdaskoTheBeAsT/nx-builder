# @testcafe-community/nx-builder 
A custom Angular/nx builder for [TestCafe](http://devexpress.github.io/testcafe/).
Serves the Angular/nx application, and then runs the TestCafe tests.  Forked from https://github.com/politie/angular-testcafe

## Install
```bash
$ npm install --save-dev @testcafe-community/nx-builder
```

## Use in angular.json
```json
{
  "projects": {
    "my-project-e2e": {
      "architect": {
        "e2e": {
          "builder": "@testcafe-community/nx-builder:testcafe",
          "options": {
            "browsers": [
              "chrome --no-sandbox",
              "firefox"
            ],
            "clientScripts":{"module":"@testing-library/dom/dist/@testing-library/dom.umd.js"},
            "src": ["e2e/*.e2e-spec.ts"],
            "video":{
              "path":"artifacts",
              "options":{
                "pathPattern":"${TEST}/${USERAGENT}/${FILE_INDEX}.mp4"
              },
              "encodingOptions":{
                "r": 20,
                "aspect": "4:3"
              }
            }
            "reporters": [
              {
                "name": "html",
                "output": "path/to/my/report.html"
              },
              {
                "name": "spec"
              }
            ]
          }
        }
      }
    }
  }
}
```
> NOTE: check [schema.json](src/testcafe/schema.json) for a list of all options

A tutorial how to use Angular and Testcafe combined with this builder can be found [here](https://medium.com/test-automation-pro/testcafe-tests-in-an-angular-project-e1d1ccc6e1cb)

## build
```bash
$ npm run build
```

## pack
```bash
$ npm pack
```

## NOT Implemented (TODO):
* remote browsers
* QR code
* ssl
