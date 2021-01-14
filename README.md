# WireMock Standalone for NPM

[![Wiremock Standalone](https://img.shields.io/maven-central/v/com.github.tomakehurst/wiremock-standalone?label=wiremock)](http://wiremock.org/docs/running-standalone/)
[![npm](https://img.shields.io/npm/dw/wiremock-standalone)](https://www.npmjs.com/package/wiremock-standalone)

This package downloads [WireMock standalone](http://wiremock.org/docs/running-standalone/) from Maven Central and provides simple CLI wrapper for NPM.

## How to use

```bash
npm i -D wiremock-standalone
# OR
yar add -D wiremock-standalone
```

Usage (as script in `package.json`):

```json
{
  "scripts": {
    "start:mock": "wiremock --root-dir ./mock"
  }
}
```

## Downloader configuration

By default, the latest stable version of WireMock JAR is downloaded from public Maven repository (`https://repo1.maven.org`).
You can override this behavior (by precedence):
- setting environment variables: `MAVEN_REPO_URL`, `WIREMOCK_VERSION`
- creating `.wiremock` configuration file in your project (JSON):
  ```json
  {
    "version": "[version]",
    "mavenRepoURL": "[custom Maven URL]"
  }
  ```
- adding `wiremock` property in your `package.json`:
  ```json
  "wiremock": {
    "version": "[version]",
    "mavenRepoURL": "[custom Maven URL]"
  }
  ```

## Runtime options

### Java arguments

You can pass options to Java runtime with `--java-arg` CLI argument. All system properties are collected and appended to wiremock's `--permitted-system-keys` option.

```bash
wiremock --java-arg -Dmy.custom.var=some-value --root-dir ./mock
```

## HOWTOs

### Passing ENV variables with [env-cmd](https://www.npmjs.com/package/env-cmd)

```bash
yarn env-cmd -f [path/to/.env] yarn wiremock --global-response-templating --verbose --root-dir ./mocks --permitted-system-keys=WIREMOCK_.*
```

## Donation

If this project help you reduce time to develop, you can give me a cup of coffee :)

[![Donate](https://img.shields.io/badge/Donate-PayPal-brightgreen.svg)](https://www.paypal.me/RafalGalka)
