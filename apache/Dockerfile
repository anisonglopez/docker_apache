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
    unzip \
    nodejs \
    npm    

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/html/
COPY ./app /var/www/html


COPY ./config/000-default.conf /etc/apache2/sites-available/000-default.conf

EXPOSE 80