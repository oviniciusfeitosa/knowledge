# Docker

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





