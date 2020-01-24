FROM composer:latest AS composer

FROM php:7.4-fpm-alpine

RUN apk add --no-cache acl make mysql-client && \
    docker-php-ext-install pdo_mysql

COPY --from=composer /usr/bin/composer /usr/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER=1
RUN composer global require "hirak/prestissimo:^0.3" --prefer-dist --no-progress --no-suggest --classmap-authoritative && \
    composer clear-cache

WORKDIR /application

CMD ["php-fpm"]
