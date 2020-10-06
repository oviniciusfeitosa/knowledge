# Docker

## Install Memcached

Insert this code inside your Dockerfile.

```bash
RUN apt-get update && apt-get install --no-install-recommends -y memcached libmemcached-tools libzip-dev zlibc zlib1g \
  && docker-php-ext-configure zip --with-libzip \
  && docker-php-ext-install zip \
  && git clone https://github.com/php-memcached-dev/php-memcached /usr/src/php/ext/memcached \
  && cd /usr/src/php/ext/memcached && git checkout -b php7 origin/php7 \
  && docker-php-ext-configure memcached \
  && docker-php-ext-install memcached
```



