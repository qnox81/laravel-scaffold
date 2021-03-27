FROM nginx:stable-alpine

RUN mkdir -p /app

RUN addgroup -g 1000 laravel && adduser -G laravel -g laravel,www-data -s /bin/sh -D laravel

RUN chown laravel:laravel /app

EXPOSE 80
