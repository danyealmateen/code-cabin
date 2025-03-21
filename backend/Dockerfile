FROM php:8.2-apache

# Installera systempaket och PHP-tillägg
RUN apt-get update && apt-get install -y \
    unzip zip curl git libpng-dev libonig-dev libxml2-dev \
    && docker-php-ext-install pdo pdo_mysql gd

# Installera Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Aktivera Apache mod_rewrite
RUN a2enmod rewrite

# Ändra Apache DocumentRoot till Laravel public/
RUN sed -i 's|DocumentRoot /var/www/html|DocumentRoot /var/www/html/public|' /etc/apache2/sites-available/000-default.conf

# Ange arbetskatalog
WORKDIR /var/www/html

# Kopiera projektfiler (om du inte använder volumes)
COPY . /var/www/html

# Sätt rättigheter för Laravel
RUN mkdir -p storage bootstrap/cache \
    && chown -R www-data:www-data /var/www/html \
    && chmod -R 775 storage bootstrap/cache

EXPOSE 80
