AliceBundle
===========

A Symfony2 bundle to help load Doctrine Fixtures with Alice

[![Build Status](https://travis-ci.org/hautelook/AliceBundle.png?branch=master)](https://travis-ci.org/hautelook/AliceBundle)
[![Scrutinizer Continuous Inspections](https://scrutinizer-ci.com/g/hautelook/AliceBundle/badges/general.png?s=fe44656b6d81a9f3a3972c2a3108231c6147ac3d)](https://scrutinizer-ci.com/g/hautelook/AliceBundle/)
[![Scrutinizer Quality Score](https://scrutinizer-ci.com/g/hautelook/AliceBundle/badges/quality-score.png?s=0b9ff0ac44085bc49fdb98f4ea1fec2fea918a39)](https://scrutinizer-ci.com/g/hautelook/AliceBundle/)


## Introduction

This bundle provides a new loader as well as an abstract `DataFixureLoader` that makes it easy for you to add fixtures
to your bundles. Additionally, the loader shares the references to your fixtures among your bundles, so that you can
use them there. Refer to the [Alice documentation](https://github.com/nelmio/alice/blob/master/README.md) for more
information.

## Installation

Simply run assuming you have installed composer.phar or composer binary (or add to your `composer.json` and run composer
install:

```bash
$ composer require hautelook/alice-bundle
```

You can follow `dev-master`, or use a more stable tag (recommended for various reasons). On the
[Github repository](https://github.com/hautelook/AliceBundle), or on [Packagist](http://www.packagist.org), you can
always find the latest tag.

Now add the Bundle to your Kernel:

```php
<?php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = array(
        // ...
        new Hautelook\AliceBundle\HautelookAliceBundle(),
        // ...
    );
}
```

## Configuration

You can configure the Seed, and the Locale that the Faker will use:

```yaml
# app/config/config.yml

hautelook_alice:
    locale: en_US   # default
    seed: 1         # default

## Usage

Simply add a loader class in your bundle, and extend the `DataFixtureLoader` class. Example

```php
<?php

namespace Acme\DemoBundle\DataFixtures\ORM;

use Hautelook\AliceBundle\Alice\DataFixtureLoader;
use Nelmio\Alice\Fixtures;

class TestLoader extends DataFixtureLoader
{
    /**
     * {@inheritDoc}
     */
    protected function getFixtures()
    {
        return  array(
            __DIR__ . '/test.yml',

        );
    }
}
```

## Future and ToDos:

- Unit and functional tests
- Clean up composer dev dependencies
