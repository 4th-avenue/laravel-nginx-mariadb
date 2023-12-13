FROM php:8.3-fpm

# COPY php.ini
COPY ./docker/php/php.ini /usr/local/etc/php/php.ini

# Composer install
COPY --from=composer:2.6.5 /usr/bin/composer /usr/bin/composer

# install Node.js
COPY --from=node:20.10 /usr/local/bin /usr/local/bin
COPY --from=node:20.10 /usr/local/lib /usr/local/lib

RUN apt-get update && \
    apt-get -y install \
    git \
    zip \
    unzip \
    vim \
    libicu-dev \
    && docker-php-ext-install pdo_mysql bcmath intl && \
    pecl install xdebug && \
    docker-php-ext-enable xdebug

WORKDIR /var/www/html