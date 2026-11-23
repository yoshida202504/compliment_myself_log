FROM php:8.3-apache
RUN apt-get update && apt-get install -y git unzip libzip-dev \
 && docker-php-ext-install pdo_mysql zip
RUN a2enmod rewrite
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer
ENV APACHE_DOCUMENT_ROOT=/var/www/html/public
RUN sed -ri 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
WORKDIR /var/www/html