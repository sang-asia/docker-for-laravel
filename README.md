# README

Related link: [Docker Compose for Laravel project](https://sang.asia/tips/docker-compose-for-laravel-project/)

## Introduction

Docker environment for Laravel project: `nginx:alpine`, `php:7.4.6-fpm`, `mysql:8.0.19`, `phpmyadmin/phpmyadmin:latest`.

Installed PHP extensions: `pdo_mysql`, `intl`, `opcache`, `gd`, `bcmath`, `mysqli`, `xdebug`.

## Config

Open `.env` file to change your project name / Web Port / PMA Port / MySQL Password.

Open `conf/nginx/app.conf` and change `fastcgi_pass` from:

```
fastcgi_pass docker-laravel-php:9000;
```

to:

```
fastcgi_pass your-project-php:9000;
```

Open `conf/php/docker-php-ext-xdebug.ini` to configure/view xdebug config. By default, it will connect to IDE via port 9001 with default `xdebug.idekey=docker-laravel-php`.

In `src` folder, I also keep the PhpStorm IDE config folder (`.idea` folder). So, you can open `src` folder with PhpStorm and get started.

**Notice**: when configuring PhpStorm, you need to restart IDE before connect to xdebug.

## Start / Stop

Create containers: `docker-compose up -d`.

Remove containers: `docker-compose down --remove-orphans`.

Start containers (after stopped): `docker-compose start`.

Stop containers (after started): `docker-compose stop`.

Restart containers (while running): `docker-compose restart`.

## Rebuild

After changed content of php.dockerfile you need to rebuild image before restart containers.

To rebuild image, run command: `docker-compose build`.

## Source

Put your Laravel project in `src` folder. Nginx root has been mapped to `public` folder, you don't need to do anything else.
