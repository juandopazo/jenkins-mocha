# jenkins-mocha

Single command to run your Mocha unit tests with both XUnit and LCov output (for Jenkins).

[![wercker status](https://app.wercker.com/status/9dbbc768df19ca2d2c6a87a99dc67713/m "wercker status")](https://app.wercker.com/project/bykey/9dbbc768df19ca2d2c6a87a99dc67713)

## Installation

jenkins-mocha should be added to your test codebase as a dev dependency.  You can do this with:

``` shell
$ npm install --save-dev jenkins-mocha
```

Alternatively you can manually add it to your package.json file:

``` json
{
  "devDependencies" : {
    "jenkins-mocha": "latest"
  }
}
```

then install with:

``` shell
$ npm install --dev
```

## Run

jenkins-mocha should replace your mocha command in npm test

``` json
{
    "scripts": {
        "test": "jenkins-mocha test/*"
    }
}
```

Any parameters added to the command will be passed directly to mocha.

When npm-test is invoked, the module will:
 - Create XUnit test results in `$(TEST_DIR)`
 - Create LCov coverage in `$(COVERAGE_DIR)` with a HTML report at `$(COVERAGE_DIR)\lcov-report`

Default values are:
 - `$(ARTIFACTS_DIR) = ./artifacts`
 - `$(TEST_DIR) = ./$(ARTIFACTS_DIR)/test`
 - `$(COVERAGE_DIR) = ./$(ARTIFACTS_DIR)/coverage`

## Restrictions

jenkins-mocha *cannot work* if your package brings in mocha, istanbul, or spec-xunit-file.  This is due to the relative path resolution of mocha/istanbul executables and mocha reporters.

## License

[MIT](http://opensource.org/licenses/MIT) © [St. John Johnson](http://stjohnjohnson.com)
