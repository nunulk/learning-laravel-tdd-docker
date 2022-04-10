FROM php:8.0-fpm-alpine

ARG TZ

# PHP
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN apk upgrade --update && \
  apk --no-cache --update add autoconf gcc g++ make icu-dev libzip-dev tzdata oniguruma-dev && \
  cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
  echo ${TZ} > /etc/timezone && \
  docker-php-ext-install intl pdo_mysql mbstring zip bcmath

# JS
RUN apk --no-cache --update add nodejs npm yarn
