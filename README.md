# charonlab/testing

[![License](https://poser.pugx.org/charonlab/testing/license.svg)](https://packagist.org/packages/charonlab/testing)

## Installation

Use the composer to install:

```bash
composer require --dev charonlab/testing
```

## Usage 

### PHPUnit

Create a `phpunit.xml.dist` file, below is a sample configuration.

```xml
<?xml version="1.0" encoding="utf-8"?>
<phpunit xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:noNamespaceSchemaLocation="vendor/phpunit/phpunit/phpunit.xsd"
         bootstrap="vendor/autoload.php"
         colors="true"
         cacheDirectory=".phpunit.cache"
         executionOrder="depends,defects"
         requireCoverageMetadata="true"
         beStrictAboutCoverageMetadata="true"
         displayDetailsOnTestsThatTriggerNotices="true"
         displayDetailsOnTestsThatTriggerWarnings="true"
         failOnNotice="true"
         failOnWarning="true"
         failOnRisky="true"
>
    <coverage/>

    <testsuites>
        <testsuite name="Charon Test Suite">
            <directory>tests</directory>
        </testsuite>
    </testsuites>
    <source restrictDeprecations="true" restrictNotices="true" restrictWarnings="true">
        <include>
            <directory>src</directory>
        </include>
    </source>
    <php>
        <ini name="error_reporting" value="24575"/>
    </php>
</phpunit>
```

### PHPBench

Create a `phpbench.json` file, below is a sample configuration.

```json
{
  "$schema":"./vendor/phpbench/phpbench/phpbench.schema.json",

  "runner.bootstrap": "./vendor/autoload.php",
  "runner.path": "tests/Performance",
  "runner.progress": "plain",
  "runner.iterations": 20,
  "runner.revs": 1000,
  "runner.file_pattern": "*Bench.php",
  "report.generators": {

    "compressed": {
      "title": "Charon Container Benchmark Tests",
      "generator": "expression",
      "cols": [ "benchmark", "subject", "mem_peak", "mode", "mean", "best", "worst" ]
    }
  },

  "core.extensions": [
    "PhpBench\\Extensions\\XDebug\\XDebugExtension"
  ]
}
```

## Support

- [Issues](https://github.com/charonlab/testing/issues/)

## License

The MIT License (MIT). Please see [License](LICENSE) for more information.
