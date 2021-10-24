# Docker

## Docker command as an alias for Composer

{% hint style="info" %}
Put the content below inside **`~/.bashrc`** or **`~/.zshrc`**
{% endhint %}

```
alias composer='docker run --rm -v $(pwd):/app composer:1.5.1 '
```

## Docker command as an alias for PHP

{% hint style="info" %}
Put the content below inside **`~/.bashrc`** or **`~/.zshrc`**
{% endhint %}

```
 alias php='docker run --rm --name=php-cli -v $(pwd):/www matriphe/alpine-php:cli php'
```

## PHP 7.4 + Memcached

Insert this code inside your **Dockerfile:**

```bash
FROM php:7.4-apache

RUN apt-get update
RUN apt-get install -y git libmemcached-dev wget unzip
RUN apt-get install --no-install-recommends -y libzip-dev zlibc zlib1g
RUN docker-php-ext-install zip

RUN mkdir -p /usr/src/php/ext/memcached
WORKDIR /usr/src/php/ext/memcached
RUN wget https://github.com/php-memcached-dev/php-memcached/archive/v3.1.3.zip; unzip /usr/src/php/ext/memcached/v3.1.3.zip
RUN mv /usr/src/php/ext/memcached/php-memcached-3.1.3/* /usr/src/php/ext/memcached/

RUN docker-php-ext-configure memcached && docker-php-ext-install memcached \
  && docker-php-ext-install mysqli
RUN a2enmod rewrite
```

## Docker Compose + Memcached + Wordpress

{% code title="docker-compose.yml" %}
```bash
version: '2'
volumes:
  wordpress-db:
  wordpress-data:

services:
  mariadb:
    image: amd64/mariadb:10.2
    environment:
      MYSQL_DATABASE: wordpress
      MYSQL_PASSWORD: Chang3M3
      MYSQL_ROOT_PASSWORD: Change3M34ls0
      MYSQL_USER: wordpress
    volumes:
    - wordpress-db:/var/lib/mysql

  memcached:
    image: amd64/memcached:1.5

  nginx:
    build: nginx/
    image: fjudith/wordpress:nginx
    ports:
    - 32716:443/tcp
    - 32715:80/tcp
    links:
    - memcached:memcached
    - wordpress:wordpress
    volumes:
    - wordpress-data:/var/www/html:rw

  wordpress:
    build: php7-fpm/
    image: fjudith/wordpress:php7-fpm
    environment:
      WORDPRESS_DB_HOST: mysql
      WORDPRESS_DB_NAME: wordpress
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: Chang3M3
    links:
    - memcached:memcached
    - mariadb:mysql
    volumes:
    - wordpress-data:/var/www/html

  cli:
    build: cli/
    image: fjudith/wordpress:cli
    stdin_open: true
    tty: true
    depends_on:
      - mariadb
      - wordpress
    links:
    - mariadb:mysql
    volumes:
    - wordpress-data:/var/www/html
```
{% endcode %}

