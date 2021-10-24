# How to

## PHP 7

### Install PHP 7.4 - Ubuntu below 20.04

```
sudo apt-get update
sudo apt -y install software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo apt -y install php7.4 php7.4-xml composer php7.4-mbstring
```

## PHP 8

### Install PHP 8.0 - Ubuntu

```
sudo add-apt-repository ppa:ondrej/php --force-yes
sudo apt-get update ; \
    sudo apt install php8.0-common php8.0-cli -y
php -v # Show PHP version.
php -m # Show PHP modules loaded.
```

### **Install a**dditional extensions

An example to install a few more useful extensions:

```
sudo apt install php8.0-{bz2,curl,intl,mysql,readline,xml}
```

For development environments, [code coverage tools](https://php.watch/articles/php-code-coverage-comparison) or the Xdebug debugger can be installed as well.

```
sudo apt install php8.0-pcov # PCOV code coverage tool
sudo apt install php8.0-xdebug # Xdebug debugger
```

### Purge old PHP versions

If the new installation is working as expected, you can remove the old PHP packages from the system.

```
sudo apt purge '^php7.4.*'
```

This assumes you are using PHP 7.4 as the previous version. Change `php7.4` part of the command above with the appropriate PHP version.

**References**

* ****[**PHP.Watch**](https://php.watch/articles/php-8.0-installation-update-guide-debian-ubuntu#:\~:text=Install%20PHP%208.0%20with%20CLI\&text=0%2Dcommon%20%2C%20and%20the%20CLI,m%20%23%20Show%20PHP%20modules%20loaded.)****

### Install Pear

```
sudo apt install php8.0-xml php-pear 
pear install PHP_CodeSniffer-3.5.8

# or
# composer global require squizlabs/php_codesniffer:3.5.8
```

## Commands

### PHP Built-in Server

```
# Against current folder
php -S localhost:8888 -t .
```

### Interactive mode

```
php -a
```

##

## Set Default value for env vars

```
# Constants
define('DB_HOST', getenv('MY_DB_HOST') ?: 'my-default-database-name' );

# Variables
$host = getenv('MY_DB_HOST') ?: 'my-default-database-name';
```

## Generate BCrypt hash

```
$ php -a
Interactive mode enabled

php > echo password_hash('Abcd123456', PASSWORD_DEFAULT);
$2y$10$id8o48ibJptfS7c6HL2x/uJNX4jBDSW.RYLAgx1HtG66EHvSJgM0K

```

## Execute Shell Script from PHP

```
print_r(shell_exec("cat /etc/hosts"));die;
```

## Working with Dates

```
$mytime = Carbon\Carbon::now();
echo $mytime->toDateTimeString();
```

## Use PHPCS globally

Installing globally PHPCS

```
composer global require squizlabs/php_codesniffer
```

* Know your path

```
echo $path
```

* Add the line below into your `~/.zshrc` ou `~/.bashrc`

```
export PATH="/home/$USER/.config/composer/vendor/bin:$PATH"
```

## array\_map to utf8\_encode

```
$result = array_map(function ($data) {
    return array_map('utf8_encode', $data);
}, $result);
```

##
