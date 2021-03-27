FROM php:7.3-fpm-alpine

RUN addgroup -g 1000 laravel && adduser -G laravel -g laravel,www-data -s /bin/sh -D laravel

RUN mkdir -p /app

RUN chown laravel:laravel /app

WORKDIR /app

RUN apk add --update --no-cache mariadb-client libzip docker bash $PHPIZE_DEPS \
  && apk add --update --virtual .build-deps autoconf g++ make zlib-dev curl-dev libxml2-dev libzip-dev \
  && pecl channel-update pecl.php.net \
  && pecl install -o -f redis xdebug \
  && docker-php-ext-enable redis xdebug \
  && docker-php-ext-install pdo pdo_mysql mbstring opcache tokenizer xml pcntl sockets zip \
  && apk del .build-deps \
  && rm -rf /tmp/* \
  && addgroup laravel docker

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

