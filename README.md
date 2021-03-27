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

- `yarn` container will install all packages from `package.json`

- wait until `mysql` and `yarn` containers stop initial boot

3. run Laravel migration

```bash
$ docker-compose run artisan migrate
```

4. generate Laravel key for docker env

```bash
$ docker-compose run artisan key:gen
```

5. compile asserts

```bash
$ docker-compose run yarn dev
```

## Jetstream + Intertia + Tailwind

1. install Jetsream
```bash
$ docker-compose run composer require laravel/jetstream
```

2. Install Jetstream With Inertia
```bash
$ docker-compose run artisan jetstream:install inertia
```

3. install dependencies
```bash
$ docker-compose run yarn
```

4. compile assets
```bash
$ docker-compose run yarn dev
```

5. run migration
```bash
$ docker-compose run artisan migrate
```
## Licence
MIT :)
