FROM php:7.3-fpm

# RUN docker-php-ext-install mysqli pdo_mysql
RUN usermod -u 1000 www-data

RUN apt-get update && apt-get install git zip unzip -y

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY --chown=www-data:www-data composer.* ./

RUN composer install --no-scripts --no-autoloader

COPY --chown=www-data:www-data . .

RUN composer dump-autoload --optimize
