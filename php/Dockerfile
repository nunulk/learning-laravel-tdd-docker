FROM php:7.3-fpm-alpine

ARG TZ

# PHP
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer

RUN apk upgrade --update && \
  apk --no-cache --update add autoconf gcc g++ make icu-dev libzip-dev tzdata && \
  cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
  echo ${TZ} > /etc/timezone && \
  docker-php-ext-install intl pdo_mysql mbstring zip bcmath && \
  curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
  composer config -g repos.packagist composer https://packagist.jp && \
  composer global require hirak/prestissimo

# JS
RUN apk --no-cache --update add nodejs nodejs-npm yarn
