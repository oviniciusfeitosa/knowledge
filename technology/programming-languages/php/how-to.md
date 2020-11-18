# How to

## Install PHP 7.4 - Ubuntu below 20.04

```text
sudo apt-get update
sudo apt -y install software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo apt -y install php7.4 php7.4-xml composer php7.4-mbstring
```

## Install Composer

```text
curl -sS https://getcomposer.org/installer | php
mv composer.phar /usr/local/bin/composer
```

## Set Default value for env vars

```text
# Constants
define('DB_HOST', getenv('MY_DB_HOST') ?: 'my-default-database-name' );

# Variables
$host = getenv('MY_DB_HOST') ?: 'my-default-database-name';
```

## PHP Built-in Server

```text
# Against current folder
php -S localhost:8888 -t .
```

## Interactive mode

```text
php -a
```

## Generate BCrypt hash

```text
$ php -a
Interactive mode enabled

php > echo password_hash('Abcd123456', PASSWORD_DEFAULT);
$2y$10$id8o48ibJptfS7c6HL2x/uJNX4jBDSW.RYLAgx1HtG66EHvSJgM0K

```

## Execute Shell Script from PHP

```text
print_r(shell_exec("cat /etc/hosts"));die;
```

## Working with Dates

```text
$mytime = Carbon\Carbon::now();
echo $mytime->toDateTimeString();
```

