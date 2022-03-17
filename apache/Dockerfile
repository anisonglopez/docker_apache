FROM php:7.4.28-apache

RUN apt-get update -y && apt-get install -y libmcrypt-dev openssl
RUN docker-php-ext-install -j$(nproc) pdo pdo_mysql mysqli

RUN apt-get update && apt-get install -y libmcrypt-dev openssl \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    libzip-dev \
    zip \
    unzip \
    nodejs \
    npm    \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install zip opcache 
    

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/html/
COPY ./app /var/www/html


# COPY ./config/000-default.conf /etc/apache2/sites-available/000-default.conf
# ADD   ./config/php.ini "$PHP_INI_DIR/php.ini"

ENV APACHE_DOCUMENT_ROOT=/var/www/html/public
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf

# 3. mod_rewrite for URL rewrite and mod_headers for .htaccess extra headers like Access-Control-Allow-Origin-
RUN a2enmod rewrite headers

# 4. start with base php config, then add extensions
# RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"



EXPOSE 80