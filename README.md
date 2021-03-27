# Info

Scaffold for new Laravel projects. Very basic laravel app containing:

- Laravel 8.x

## Docker integration

I've added Docker for local development on Mac with following containers:
- app (php-fpm:7.3)
- mysql (mariaDB:10.5)
- nginx
- composer
- artisan 
- yarn

Details in [docker-composer.yml](docker-composer.yml) file.

## Installation

1. copy project

```bash
$ composer create-project --prefer-dist qnox81/laravel-scaffold app-name
```

2. edit `.env` and set app `COMPOSE_PROJECT_NAME` and adjust `APP_DOCKER_*` variables and start docker containers

```bash
$ docker-compose up -d
```
- `yarn` container will install all packages from `packaga.json`

3. install composer dependecies

```bash
$ docker-compose run composer install 
```

4. run artisan commands

```bash
$ docker-compose run artisan key:gen 
```

```bash
$ docker-compose run artisan migrate
```

## Licence
MIT :)
