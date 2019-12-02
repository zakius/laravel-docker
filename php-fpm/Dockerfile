FROM php:fpm

RUN apt-get update \
    && apt-get install --no-install-recommends -y zlib1g-dev libpq-dev git libicu-dev libxml2-dev zip unzip libzip-dev libpng-dev \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl gd pdo_pgsql zip \
    && pecl install redis \
    && docker-php-ext-enable redis \
    && php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php \
    && php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer

WORKDIR /var/www/html

