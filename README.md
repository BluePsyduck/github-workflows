# BluePsyduck's Github Workflows

This repository contains the Github workflows, reused across my projects.

## CI PHP General

This workflow checks general things about the PHP project, including composer validation, coding guidelines using phpcs,
and static analysis through PHPStan.

The following variables can be used with the workflow:

| Variable    | Default | Description                                        |
|-------------|---------|----------------------------------------------------|
| extensions  | ""      | The comma-separated list of extensions to install. |
| php-version | "8.1"   | The PHP version to use for the checks.             |

Note hat the PHP version is expected as a string (not as a number) to be consistent with the other workflow.

## CI PHP Tests

This workflow executes the PHPUnit tests of the project. It will automatically detect all suites configured for PHPUnit,
and execute them in separate jobs. It also supports checking coverage for one of the suites.

| Variable            | Default       | Description                                                                   |
|---------------------|---------------|-------------------------------------------------------------------------------|
| extensions          | ""            | The comma-separated list of extensions to install.                            |
| php-versions        | "8.1 8.0 7.4" | The PHP versions to execute the tests in specified as space-separated string. |
| min-php-version     | "all"         | The minimal PHP version to use when using the default versions.               |
| suite-with-coverage | "unit-test"   | The PHPUnit test suite which should be checked for coverage.                  |

## Example

```yaml
jobs:
  call-workflow-ci-php-general:
    name: General
    uses: BluePsyduck/github-workflows/.github/workflows/ci-php-general.yaml@v1

  call-workflow-ci-php-tests:
    name: Tests
    uses: BluePsyduck/github-workflows/.github/workflows/ci-php-tests.yaml@v1
    with:
      min-php-version: "8.0"
```
