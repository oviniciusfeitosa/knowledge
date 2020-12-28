# Laravel

## Topics

* \*\*\*\*[**Jet Stream**](jet-stream.md)\*\*\*\*
* \*\*\*\*[**Know Issues**](known-issues-1.md)\*\*\*\*
* \*\*\*\*[**Sail**](sail.md)\*\*\*\*
* \*\*\*\*[**Sanctum**](sanctum.md)\*\*\*\*
* \*\*\*\*[**Valet**](valet.md)\*\*\*\*

## Laravel 8

### Create a simple app

```text
curl -s https://laravel.build/my-simple-app | bash
cd my-simple-app
./vendor/bin/sail up
```

### Create a simple app using Composer

```text
composer create-project laravel/laravel my-simple-app
cd my-simple-app
php artisan serve
```

### Create a simple app using t**he Laravel Installer**

You may install the Laravel Installer as a global Composer dependency:

```text
composer global require laravel/installer
laravel new my-simple-app
php artisan serve
```

{% hint style="info" %}
Make sure to place Composer's system-wide vendor bin directory in your `$PATH` so the `laravel` executable can be located by your system. This directory exists in different locations based on your operating system; however, some common locations include:

* macOS: `$HOME/.composer/vendor/bin`
* Windows: `%USERPROFILE%\AppData\Roaming\Composer\vendor\bin`
* GNU / Linux Distributions: `$HOME/.config/composer/vendor/bin` or `$HOME/.composer/vendor/bin`
{% endhint %}

## Recommended

* \*\*\*\*[**Laracasts**](https://laracasts.com)\*\*\*\*



