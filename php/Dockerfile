FROM php:7.3-fpm

RUN docker-php-ext-install mysqli
RUN docker-php-ext-install pdo_mysql

WORKDIR /home/sites/
RUN apt-get update
RUN apt-get install sudo
