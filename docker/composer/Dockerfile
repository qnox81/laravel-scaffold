FROM composer:latest

LABEL MANGOdev <team@mangodev.pl>

RUN addgroup -g 1000 laravel && adduser -G laravel -g laravel -s /bin/sh -D laravel

WORKDIR /app

VOLUME /app
