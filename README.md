# README

## Introduction

Docker environment for Laravel project: `nginx:alpine`, `php:7.4.6-fpm`, `mysql:8.0.19`, `phpmyadmin/phpmyadmin:latest`.

Installed PHP extensions: `pdo_mysql`, `intl`, `opcache`, `gd`, `bcmath`, `mysqli`.

## Config

Open `.env` file to change your project name / Web Port / PMA Port / MySQL Password.

Open `conf/nginx/app.conf` and change `fastcgi_pass` from:

```
fastcgi_pass docker-laravel-php:9000;
```
```
fastcgi_param PHP_VALUE 'xdebug.idekey=docker-laravel-php';
```

to:

```
fastcgi_pass your-project-php:9000;
```
```
fastcgi_param PHP_VALUE 'xdebug.idekey=your-project-php';
```

## Start / Stop

Start: `docker-compose up -d`.

Stop: `docker-compose down --remove-orphans`.

## Rebuild

After changed content of php.dockerfile you need to rebuild image before restart containers.

To rebuild image, run command: `docker-compose build`.

## Source

Put your Laravel project in `src` folder. Nginx root has been mapped to `public` folder, you don't need to do anything else.
