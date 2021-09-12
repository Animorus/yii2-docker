This is a fork of the official  [Yii 2.0 Framework](http://www.yiiframework.com/) image [repository](https://github.com/yiisoft/yii2-docker). The functionality has been changed to suit my personal needs.

## Features:
- Apache only
- Removed flavor dockerfile
- Added mySQL
- Added phpMyAdmin
- Disabled mongoDB

## About

These Docker images are built on top of the official PHP Docker image, they contain additional PHP extensions required to run Yii 2.0 framework, but no code of the framework itself.
The `Dockerfile`(s) of this repository are designed to build from different PHP-versions by using *build arguments*.

### Available versions for `yiisoftware/yii2-php`

```
8.0
7.4 
```

#### Deprecated or EOL versions

```
7.3
7.2, 7.1, 7.0, 5.6
```

## Setup

    cp .env-dist .env

Adjust the versions in `.env` if you want to build a specific version.

## Configuration

- `PHP_ENABLE_XDEBUG` whether to load an enable Xdebug, defaults to `0` (false)
- `PHP_USER_ID` (Debian only) user ID, when running commands as webserver (`www-data`), see also [#15](https://github.com/yiisoft/yii2-docker/issues/15)
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

- Depending on the (Debian) base-image (usually PHP <7.4) you might need to set `X_LEGACY_GD_LIB=1`
