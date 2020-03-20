FROM php:7.4-fpm

WORKDIR /root
RUN apt-get update

# 시간대 설정
RUN ln -sf /usr/share/zoneinfo/Asia/Seoul /etc/localtime

# php package 설치를 위해 필요한 library 설치
RUN apt-get install -y curl libpng-dev zlib1g-dev libzip-dev libonig-dev \
    libcurl4-openssl-dev pkg-config libxml2-dev libssl-dev vim

RUN docker-php-ext-install zip pdo_mysql mysqli

RUN CFLAGS="-I/usr/src/php" docker-php-ext-install json curl phar \
    dom xml intl xmlreader ctype session \
    mbstring gd

# Composer 설치
RUN export COMPOSER_ALLOW_SUPERUSER=1
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/bin/composer

