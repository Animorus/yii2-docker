This is a fork of the official  [Yii 2.0 Framework](http://www.yiiframework.com/) image [repository](https://github.com/yiisoft/yii2-docker). The functionality has been changed to suit my personal needs.

## Features:
- Apache
- Debian
- Added mySQL
- Added phpMyAdmin
- Disabled mongoDB

## About

These Docker images are built on top of the official PHP Docker image, they contain additional PHP extensions required to run Yii 2.0 framework, but no code of the framework itself.
The `Dockerfile`(s) of this repository are designed to build from different PHP-versions by using *build arguments*.

## Setup

    cp .env-dist .env

## Configuration

- `PHP_BASE_IMAGE_VERSION` - PHP build version. For example, `7.4`, `8.0`
- `PHP_ENABLE_XDEBUG` - whether to load an enable Xdebug. Default value `1` (true) 
- `PHP_USER_ID` - user ID, when running commands as webserver (`www-data`), see also [#15](https://github.com/yiisoft/yii2-docker/issues/15)
- `MYSQL_ROOT_PASSWORD` - this variable is mandatory and specifies the password that will be set for the root superuser account.
- `MYSQL_DATABASE` - this variable is optional and allows you to specify the name of a database to be created on image startup


## Building

    docker-compose build

## Testing

    docker-compose run --rm php php /tests/requirements.php

### Xdebug

To enable Xdebug, set `PHP_ENABLE_XDEBUG=1` in .env file

Xdebug is configured to call ip `xdebug.remote_host` on `9005` port (not use standard port to avoid conflicts),
so you have to configure your IDE to receive connections from that ip.

## FAQ

- Depending on the PHP base-image (usually version <7.4) you might need to set `X_LEGACY_GD_LIB=1`
