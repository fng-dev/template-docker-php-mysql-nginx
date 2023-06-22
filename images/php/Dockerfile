FROM php:8.1-fpm
RUN apt update
RUN apt install -y git
RUN apt install -y zip
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php
RUN mv composer.phar /usr/local/bin/composer
RUN docker-php-ext-install pdo pdo_mysql

RUN apt-get clean && apt-get update \
    &&  apt-get install -y --no-install-recommends \
        locales \
        apt-utils \
        git \
        libicu-dev \
        g++ \
        libpng-dev \
        libxml2-dev \
        libzip-dev \
        libonig-dev \
        libxslt-dev \
        unzip \
        libpq-dev \
        nodejs \
        npm \
        wget \
        apt-transport-https \
        lsb-release \
        ca-certificates \
        iputils-ping \
        net-tools
RUN docker-php-ext-install gd
WORKDIR /var/www