# A set of interfaces and methods to clean up your application's tax calculations

[![Latest Version on Packagist](https://img.shields.io/packagist/v/spatie/tax-calculator.svg?style=flat-square)](https://packagist.org/packages/spatie/tax-calculator)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)
[![Build Status](https://img.shields.io/travis/spatie/tax-calculator/master.svg?style=flat-square)](https://travis-ci.org/spatie/tax-calculator)
[![SensioLabsInsight](https://img.shields.io/sensiolabs/i/xxxxxxxxx.svg?style=flat-square)](https://insight.sensiolabs.com/projects/xxxxxxxxx)
[![Quality Score](https://img.shields.io/scrutinizer/g/spatie/tax-calculator.svg?style=flat-square)](https://scrutinizer-ci.com/g/spatie/tax-calculator)
[![Total Downloads](https://img.shields.io/packagist/dt/spatie/tax-calculator.svg?style=flat-square)](https://packagist.org/packages/spatie/tax-calculator)

A set of interfaces and methods to clean up your application's tax calculations. The `TaxCalculation` class allows you to do calculations with plain numbers and objects that implement the `HasTax` interface on the fly.

```php
use Spatie\TaxCalculator\TaxCalculation;

$items = $myCart->getItems(); // Should return an array of items that implement `HasTax`

TaxCalculation::fromCollection($items)->basePrice(); // 10.00
TaxCalculation::fromCollection($items)->taxPrice(); // 2.10
TaxCalculation::fromCollection($items)->taxedPrice(); // 12.10

$delivery = TaxCalculation::fromTaxedPrice(7.50, 0.21);

TaxCalculation::fromCollection($items)->add($delivery)->taxedPrice(); // 19.60
```

Spatie is a webdesign agency based in Antwerp, Belgium. You'll find an overview of all our open source projects [on our website](https://spatie.be/opensource).

## Installation

You can install the package via composer:

``` bash
composer require spatie/tax-calculator
```

## Usage

### Interfaces

#### `Spatie\TaxCalculator\HasTax`

```php
public function basePrice(): float;
public function taxedPrice(): float;
public function taxPrice(): float;
```

- `basePrice`: The item's price excluding taxes
- `taxedPrice`: The item's price including taxes
- `taxPrice`: The item's tax amount (`= taxedPrice() - basePrice()`)

#### `Spatie\TaxCalculator\HasTaxWithRate`

```php
public function taxRate(): float;
```

`HasTaxWithRate` extends `HasTax`, and also has a `taxRate` method. This is useful for items that have a fixed tax rate, but can't be used on collections that contain items with various rates.

### Traits

### `Spatie\TaxCalculator\Traits\HasTaxWithRate`

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Testing

``` bash
$ composer test
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

## Security

If you discover any security related issues, please email freek@spatie.be instead of using the issue tracker.

## Credits

- [Sebastian De Deyne](https://github.com/sebastiandedeyne)
- [All Contributors](../../contributors)

## About Spatie
Spatie is a webdesign agency based in Antwerp, Belgium. You'll find an overview of all our open source projects [on our website](https://spatie.be/opensource).

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
