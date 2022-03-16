FROM php:7.4.28-apache

RUN apt-get update -y && apt-get install -y libmcrypt-dev openssl
RUN docker-php-ext-install -j$(nproc) pdo pdo_mysql mysqli

RUN apt-get update && apt-get install -y libmcrypt-dev openssl \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip

RUN apt-get install -y git-core curl build-essential openssl libssl-dev \
 && git clone https://github.com/nodejs/node.git \
 && cd node \
 && ./configure \
 && make \
 && sudo make install

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/html/public
COPY ./app /var/www/html

EXPOSE 80