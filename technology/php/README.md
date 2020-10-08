# PHP

## Install PHP 7.4 - Ubuntu below 20.04

```text
sudo apt-get update
sudo apt -y install software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo apt -y install php7.4 php7.4-xml composer php7.4-mbstring
```

## Set Default value for env vars

```text
# Constants
define('DB_HOST', getenv('MY_DB_HOST') ?: 'my-default-database-name' );

# Variables
$host = getenv('MY_DB_HOST') ?: 'my-default-database-name';
```



