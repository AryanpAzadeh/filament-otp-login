# OTP Login for FilamentPHP

[![Latest Version on Packagist](https://img.shields.io/packagist/v/afsakar/filament-otp-login.svg?style=flat-square)](https://packagist.org/packages/afsakar/filament-otp-login)
[![Total Downloads](https://img.shields.io/packagist/dt/afsakar/filament-otp-login.svg?style=flat-square)](https://packagist.org/packages/afsakar/filament-otp-login)

![Screenshot](https://banners.beyondco.de/Filament%20OTP%20Login.png?theme=light&packageManager=composer+require&packageName=afsakar%2Ffilament-otp-login&pattern=architect&style=style_1&description=Simple+OTP+Login+for+FilamentPHP&md=1&showWatermark=0&fontSize=100px&images=login)


This package is an OTP Login for FilamentPHP. It is a simple package that allows you to login to your FilamentPHP application using OTP.

## Installation

You can install the package via composer:

```bash
composer require afsakar/filament-otp-login
```

You can publish and run the migrations with:

```bash
php artisan vendor:publish --tag="filament-otp-login-migrations"
php artisan migrate
```

You can publish the config and translations files with:

```bash
php artisan vendor:publish --tag="filament-otp-login-config"
php artisan vendor:publish --tag="filament-otp-login-translations"
```

Optionally, you can publish the views using

```bash
php artisan vendor:publish --tag="filament-otp-login-views"
```

This is the contents of the published config file:

```php
return [
    'table_name' => 'otp_codes', // Table name to store OTP codes

    'user_model' => env('OTP_LOGIN_USER_MODEL',  'App\\Models\\User',), // User model to store OTP codes

    'otp_code' => [
        'length' => env('OTP_LOGIN_CODE_LENGTH', 6), // Length of the OTP code
        'expires' => env('OTP_LOGIN_CODE_EXPIRES_SECONDS', 120), // Expiration time of the OTP code in seconds
    ],
];

```

## Usage

Just register the `Afsakar\FilamentOtpLogin\FilamentOtpLoginPlugin` plugin in the your panel provider file.

```php
use Afsakar\FilamentOtpLogin\FilamentOtpLoginPlugin;

    public function panel(Panel $panel): Panel
    {
        return $panel
            ->plugins([
                FilamentOtpLoginPlugin::make(),
            ]);
    }
```

## Testing

```bash
composer test
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Contributing

Please see [CONTRIBUTING](.github/CONTRIBUTING.md) for details.

## Security Vulnerabilities

Please review [our security policy](../../security/policy) on how to report security vulnerabilities.

## Credits

- [Azad Furkan ŞAKAR](https://github.com/afsakar)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
