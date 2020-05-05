# Sign in with apple

Good solution for implementation auth with apple for REST API. This package is extension of laravel/socialite package, it adds custom apple provider to socialite. It allows you to to create auth with apple flow using only apple's access_token. Package will check if token was not modified by validating token signature.

## Installation

You can install the package via composer:

```bash
composer require nerdzlab/laravel-socialite-apple-sign-in
```

You may publish config if needed:
```bash
 php artisan vendor:publish --provider="Nerdzlab\LaravelSocialiteAppleSignIn\LaravelSocialiteAppleSignInServiceProvider" --tag="config"
```

## Usage

To get started you need to add credentials for the apple service in your services config file.

``` php
'apple' => [
    'client_id' => 'YOUR_APP_ID'
],
```

Package automatically adds 'apple' driver to Socialite. After that you can obtain user data from access_token received from apple.

``` php
use Laravel\Socialite\Facades\Socialite;

$user = Socialite::driver('apple')->userFromToken($accessToken);
```

Package will cache public keys retrieved from apple during auth flow.
You may automatically cache public keys by calling command:

```bash
php artisan apple-sign-in:update-jwks
```

### Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.