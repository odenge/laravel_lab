FROM php:7.2-apache

RUN apt-get update \
    && apt-get -y -qq --no-install-recommends install vim \
    && apt-get -y -qq --no-install-recommends install libzip-dev \
    && apt-get -y -qq --no-install-recommends install unzip \
    && docker-php-ext-install pdo_mysql mysqli mbstring zip

RUN a2enmod rewrite
