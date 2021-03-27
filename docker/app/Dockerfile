FROM php:7.3-fpm-alpine

LABEL MANGOdev <team@mangodev.pl>

RUN addgroup -g 1000 laravel && adduser -G laravel -g laravel,www-data -s /bin/sh -D laravel

RUN mkdir -p /app

RUN chown laravel:laravel /app

RUN apk add --update --no-cache supervisor mariadb-client libzip docker bash curl libintl icu icu-dev imagemagick git \
  && apk add --update --virtual .build-deps autoconf g++ make zlib-dev curl-dev libxml2-dev libzip-dev bzip2-dev imagemagick-dev curl-dev $PHPIZE_DEPS\
  && pecl channel-update pecl.php.net \
  && pecl install -o -f imagick redis xdebug \
  && docker-php-ext-enable imagick redis xdebug \
  && docker-php-ext-install curl iconv pdo pdo_mysql mbstring opcache tokenizer xml pcntl json sockets zip intl \
  && apk del .build-deps \
  && rm -rf /tmp/* \
  && addgroup laravel docker

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /app
